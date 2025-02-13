---
description: >-
  Configure an email provider of your choice to send and receive email
  notifications in Appsmith
---

# Email

[Email](https://en.wikipedia.org/wiki/Email) is a widely used service to communicate with your users. You can set up email integration on your Appsmith instance to:

* Invite users to your Appsmith workspace
* Notify admins of important events & approval requests

Appsmith allows you to configure email using environment variables or the [admin settings](../admin-settings.md#using-the-admin-settings-ui).

{% embed url="https://youtu.be/NOAofPbmJWw" %}

## Configure using Environment Variables

Appsmith requires the following environment variables to be configured:

{% hint style="warning" %}
&#x20;You could start with email configuration after following the [Instance Configuration Guide](../) for your instance deployment.
{% endhint %}

| Variable                               | Description                                                                                                                                                                                             |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **APPSMITH\_MAIL\_ENABLED**            | Set it to true to enable the email service.                                                                                                                                                             |
| **APPSMITH\_MAIL\_FROM**               | Set it to the verified email of the sender.                                                                                                                                                             |
| **APPSMITH\_REPLY\_TO**                | Set it to the email that should receive replies by default.                                                                                                                                             |
| **APPSMITH\_MAIL\_HOST**               | Set it to the **SMTP Host** of the email service provider.                                                                                                                                              |
| **APPSMITH\_MAIL\_PORT**               | Set it to the **SMTP Port** available for the email service provider.                                                                                                                                   |
| **APPSMITH\_MAIL\_SMTP\_TLS\_ENABLED** | Enables transport layer security if set to **true.**                                                                                                                                                    |
| **APPSMITH\_MAIL\_SMTP\_AUTH**         | Set it to **true** to share the credentials (<mark style="color:red;">`APPSMITH_MAIL_USERNAME`</mark> **** and **** <mark style="color:red;">`APPSMITH_MAIL_PASSWORD`</mark>**)** with the SMTP server. |
| **APPSMITH\_MAIL\_USERNAME**           | Set it to the username for accessing the SMTP service provider.                                                                                                                                         |
| **APPSMITH\_MAIL\_PASSWORD**           | Set it to the password for the SMTP user. You can also set it to the API key generated by the email service provider for the SMTP user.                                                                 |

{% hint style="warning" %}
Be sure to double-check your config **** if you find that you're able to send **test** mail but **not** invites or password resets.
{% endhint %}

[Restart the Appsmith instance](../) once the environment variables are configured.

## Configure using Admin Settings

You can configure the email for your self-hosted instance using the [Admin Settings](../admin-settings.md#using-the-admin-settings-ui) page. Follow the below steps:

* Navigate to **profile** >> **Admin Settings** >> Select **Email.**

![Add Configuration Details](<../../../../.gitbook/assets/Instance Configuration  Email  Configure using Admin Settings.png>)

*   Add configuration details provided by your email service provider.

    * **SMTP Host** - SMTP host of your email service provider
    * **SMTP Port** - SMTP port of your email service provider
    * **From Address** - a verified email address that will be shown in the <mark style="color:red;">`from field`</mark> when users receive an email
    * **TLS Protected Connection** - Bey default is enabled. Toggle back to disable
    * **SMTP Username** - Add the username for your email service provider
    * **SMTP Password** - Add the password for your email service provider


* Click the <mark style="color:red;">`SAVE & RESTART`</mark> button to save the configurations and restart the Appsmith instance with the updated settings.

{% hint style="success" %}
Once your instance is restarted, you can use the <mark style="color:red;">**`SEND TEST EMAIL`**</mark> button to send a test email. You should see a message at the top of the page telling you whether the test succeeded or failed. On success, you should also receive a test email in your email inbox.
{% endhint %}

## Configuration Guides&#x20;

Follow the below guides to configure popular email service providers:

{% content-ref url="sendgrid.md" %}
[sendgrid.md](sendgrid.md)
{% endcontent-ref %}

{% content-ref url="amazon-ses.md" %}
[amazon-ses.md](amazon-ses.md)
{% endcontent-ref %}

{% content-ref url="gmail.md" %}
[gmail.md](gmail.md)
{% endcontent-ref %}
