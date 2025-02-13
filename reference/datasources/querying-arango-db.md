# ArangoDB

[ArangoDB](https://www.arangodb.com) is a free and open-source native multi-model database system developed by ArangoDB GmbH. The database system supports three data models with one database core and a unified query language AQL

{% hint style="warning" %}
The following document assumes that you understand the [basics of connecting to databases on Appsmith](../../core-concepts/connecting-to-data-sources/connecting-to-databases.md#connecting-to-a-database). If not, please go over them before reading further.
{% endhint %}

## Connecting ArangoDB with Appsmith

On Appsmith, it’s pretty straightforward to establish a connection with any data source, including ArangoDB; be it on the cloud, a self-hosted instance, or a local environment.

What we need to make the connection are the endpoint, database name, and user credentials. With this in mind, let’s get started.

* On your Appsmith application, click on the `+` icon next to Datasources on the left navigation bar under Page1
* Now, navigate to the Create New tab and choose ArangoDB data source.

![](../../.gitbook/assets/Adding\_datasouce\_arangodb.jpeg)

* When you’re using ArangoDB cloud or a self-hosted instance, all these details can be found under the instance settings.

![](<../../.gitbook/assets/Arango\_self\_hosted (1).jpeg>)

### Connection Settings

Appsmith needs the following parameters for connecting to an Arango database:

{% hint style="success" %}
All required fields are suffixed with an asterisk (\*).
{% endhint %}

#### **Connection**

You need to fill in the following parameters:

* **Host Address\* / Port:** Fill in the database host’s address and port. If you don’t specify a port, Appsmith will try to connect to port 8529.
* **Database Name\*:** Fill in the name of the database that you want to connect to. This is your database’s name.

#### **Authentication**

You need to fill in the following parameters:

* **Username\*:** Fill in the username required for authenticating connection requests to your database.
* **Password\*:** Fill password required for authenticating connection requests for the given username to the database.

#### **SSL**

The SSL Mode can be set to one of the following values:

* **`Default`**: Same as `Disabled`.
* **`Enabled`**: Rejects the connection if SSL is not available.
* **`Disabled`**: Connects without SSL using a plain unencrypted connection.

{% hint style="warning" %}
Ensure that the SSL mode is enabled so as to establish a secure connection.
{% endhint %}

Here’s what the configuration will look like:

![](../../.gitbook/assets/Arango\_configuration.jpeg)

Next, click on the `Test` button at the bottom right of the screen. This will help you with understanding whether your configuration is valid or not. If it returns a successful message, hit the ‘Save’ button to establish a secure connection between Appsmith and ArangoDB.

## Using Queries in applications

Once you have successfully run a Query, you can use it in your application to

* [Display Data](../../core-concepts/data-access-and-binding/displaying-data-read/)
* [Capture Data](../../core-concepts/data-access-and-binding/capturing-data-write/)
