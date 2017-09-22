---
title: [Browser untrusted connection error]
tags:
keywords: tbd
last_updated: tbd
sidebar: mydoc_sidebar
---
If you are not using a SSL certificate for authentication, users will see an untrusted connection error in their browser when accessing ThoughtSpot. The error looks slightly different depending upon the Web browser being used.

ThoughtSpot uses secure HTTP (the HTTPS protocol) for communication between the browser and ThoughtSpot. By default there is no SSL certificate for authentication. This must be added by the site administrator. If the site administrator has not added the certificate, the browser warns the user.

|Browser|Warning|
|-------|-------|
|Google Chrome|The site's security certificate is not trusted!|
|Mozilla Firefox|This Connection is Untrusted|

If you see the warning message, choose one of the following options:

-   Ask the site administrator to install the certificate.
-   Ask the site administrator to turn off SSL using this command in the shell on the ThoughtSpot instance:

    ```
    $ tscli ssl off
    ```

-   You can choose to ignore the message, and access ThoughtSpot without SSL.