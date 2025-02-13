# How to Use the Camera/Image Widget to Upload/Download Images?

[Amazon S3](https://aws.amazon.com/s3/?nc2=type\_a) (Simple Storage Service) provides object storage built for storing and recovering any amount of information or data from anywhere over the internet. It provides this storage through a web services interface.

#### **What you'll learn**&#x20;

In this guide, you would learn:&#x20;

* How to connect and configure the S3 datasource.&#x20;
* How to use the Image and Camera widget.&#x20;
* How to upload/download images using S3.

## Create S3 Datasource

To add an S3 datasource, navigate to **Explorer** >> Click plus sign (**+**) (next to S3)>> **Select S3 under Databases**. Once your S3 datasource has been created, follow these [instructions ](https://docs.appsmith.com/reference/datasources/querying-amazon-s3#connection-settings)to connect your app to the S3 database.

{% hint style="info" %}
To upload your data to Amazon S3, you must first create an Amazon S3 bucket in one of the AWS Regions. [Create a new bucket.](https://docs.aws.amazon.com/AmazonS3/latest/userguide/create-bucket-overview.html)
{% endhint %}

## Upload Image Using Camera Widget

The camera widget powers you to capture images and videos from your applications and share the data for further use. In this section, you will learn how you can upload images/videos to Amazon S3.

{% embed url="https://youtu.be/v43gTz_4Jck" %}

* Drag and drop the [Camera widget](https://docs.appsmith.com/reference/widgets/camera) onto the canvas.&#x20;
* Click on the **+** icon next to the **queries/js** and choose your S3 datasource.&#x20;
* Rename the query.&#x20;
* From the Commands drop-down, Select the method **Create a new file.**

You can pass the below parameters to **Create a new file.**&#x20;

* **Bucket Name:** The object key (or key name) uniquely identifies the object in an Amazon S3 bucket.
* **File Path:** Path of the location you want to store the file. ex. images/any.

{% hint style="info" %}
Intermediate folders not existing will be automatically created.
{% endhint %}

* **File Data Type:** You can choose between Base64 and text as your file data type. You should select base64 when uploading data from the camera widget.
* **Expiry Duration of Signed URL (Minutes):** The timestamp at which the signed URL would expire.

{% hint style="info" %}
The maximum expiration time for a signed URL is one week from the time of creation.
{% endhint %}

* **Content**: You can manually add data into the Content field by writing an object with a text and data property or you can fetch data from the camera widget like below:

```
{
	"data": "{{Camera1.imageDataURL}}"
}
```

Once you have added all the required parameters:

* Open the Camera widget property pane.
* In the **OnImageSave** event, choose your query from the "**execute a query**" option.&#x20;

When you capture and save the image, your **upload\_image** query is executed. You can visit the [S3 console](https://s3.console.aws.amazon.com/s3/home) to see the uploaded media.

## Upload Image Using Image Widget

The Image widget displays the images in your app. Images must have a valid base64 or a URL. You can follow similar steps to the image widget.

* Drag and drop the [Image widget](https://docs.appsmith.com/reference/widgets/image) onto the canvas.
* Now set the image URL in the Image property pane.&#x20;
* Click on the **+** icon next to the **queries/js** and choose your **S3 datasource.**&#x20;
* Rename the query.&#x20;
* From the Commands drop-down, Select the method **Create a new file.**

{% hint style="info" %}
You should select **base64** as _File Data Type_ when uploading data from the image widget.
{% endhint %}

<figure><img src="../../.gitbook/assets/uploads31.PNG" alt=""><figcaption></figcaption></figure>

In the content body, add the following:

```
{
	"data": "{{Image1.image}}"
}
```

Once you have added all the required parameters:

* Now, set the Image Widget's **onClick** event to **execute a query**, and choose your query.&#x20;

Your image will be stored in the S3 database once you run this query. Let's look at how to fetch an image from the S3 database.

## Download The Image

#### Fetch Single File

{% embed url="https://youtu.be/dVZEd8p0Y2c" %}

* Click on the + icon next to the **queries/js** and choose your **S3 datasource.**
* Rename the query.
* From the Commands drop-down, Select the method **Read file.**

You can pass the below parameters to **Read a file.**&#x20;

* **Bucket Name:** Name of the bucket where the image is stored.
* **File Path**: Path of the image you want to fetch. ex. images/name.
* **File Data Type**: You should select base64 to display the image.

Once you have added all the required parameters:

* Drag and drop the[ Image widget](https://docs.appsmith.com/reference/widgets/image) onto the canvas.
* In the Image property pane, add:

```
{{<your_query_name>.data.fileData}}
```

#### Fetch All Files

{% embed url="https://youtu.be/UzV5LZ0kvDQ" %}

* Click on the + icon next to the **queries/js** and choose your **S3 datasource.**&#x20;
* Rename the query.&#x20;
* From the Commands drop-down, Select the method **List files** in the bucket.&#x20;
* Add the **bucket name.**&#x20;
* Now, run the query.

Now, open the query window and select the table option on the right-side property pane. It would automatically add a table widget to your canvas.

{% hint style="info" %}
Bind the query’s response to the Table using JavaScript in the Table Data Property **`{{list_files.data}}`**.
{% endhint %}

Now your table should list all the files present in your S3 bucket.

You can use an image widget to display images listed in the table widget. You can follow this [guide ](https://docs.appsmith.com/learning-and-resources/how-to-guides/how-to-upload-to-s3)to learn more.

#### Download Files

* Open the image property pane.&#x20;
* Click on the **JS** button next to the **onClick** event and write the following JavaScript query:

```
{{download(atob(Fetch_image.data.fileData),'Testname','image/png')}}
```

Now, your image will be downloaded when you click on the image widget.

{% hint style="info" %}
You can check this [Guide ](how-to-upload-to-s3.md)to learn more about Upload/Download Files from S3.&#x20;
{% endhint %}

With Appsmith S3 integration, it is possible to create apps that seamlessly connect with the S3 database and provide additional flexibility for updating and analyzing data.

## Using Queries in applications&#x20;

Once you have successfully run a Query, you can use it in your application to:

* [Display Data ](../../core-concepts/data-access-and-binding/displaying-data-read/)
* [Capture Data ](../../core-concepts/data-access-and-binding/capturing-data-write/capture-form-data.md)
* [Execute Queries](../../core-concepts/data-access-and-binding/querying-a-database/)
