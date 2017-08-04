---
title: [elephant]
tags: [formatting]
keywords: notes, tips, cautions, warnings, admonitions
last_updated: July 3, 2016
summary: "blerg"
sidebar: mydoc_sidebar
---
# Configure SAML

ThoughtSpot can use Security Assertion Markup Language \(SAML\) to authenticate users. You can set up SAML through the shell on ThoughtSpot using a tscli based configurator.

Before configuring SAML, you will need this information:

-   IP of the server where your ThoughtSpot instance is running.
-   Port of the server where your ThoughtSpot instance is running.
-   Protocol, or the authentication mechanism for ThoughtSpot.
-   Unique service name that is used as the unique key by IDP to identify the client.

    It should be in the following format: `urn:thoughtspot:callosum:saml`

-   Allowed skew time, which is the time after authentication response is rejected and sent back from the IDP. It is usually set to 86400.
-   The absolute path to the idp-meta.xml file. This is needed so that the configuration persists over upgrades.
-   This configurator also checks with the user if internal authentication needs to be set or not. This internal authentication mechanism is used to authenticate tsadmin, so set it to true if you do not know what it does.

Use this procedure to set up SAML on ThoughtSpot for user authentication. Note that this configuration persists across software updates, so you do not need to reapply it if you update to a newer release of ThoughtSpot.

1.  [Log in to the Linux shell using SSH](../../shared/conrefs/../../admin_guide/setup/login_console.html).
2.   Execute the command to launch the interactive SAML configuration: 

    ```
    tscli saml configure
    ```

3.   Complete the configurator prompts with the information you gathered above. 
4.   When the configuration is complete, open a Web browser and go to the ThoughtSpot login page. It should now show the Single Sign On option. 
