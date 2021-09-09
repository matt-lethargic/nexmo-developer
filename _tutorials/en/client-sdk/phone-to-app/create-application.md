---
title: Create a Vonage Application
description: In this step you learn how to create a Vonage Application.
---

# Create your Vonage Application

In this step you will create a Vonage [Application](/conversation/concepts/application) capable of in-app voice communication use cases.

Open a new terminal and, if required, navigate to your project directory.

Create a Vonage application by copying and pasting the command below into terminal Make sure to change the values of `--voice_answer_url` and `--voice_event_url` arguments, by replacing `SUBDOMAIN` with the actual value used in the previous step:

``` shell
vonage apps:create phone-to-app-tutorial --voice_answer_url=https://SUBDOMAIN.loca.lt/voice/answer --voice_event_url=https://SUBDOMAIN.loca.lt/voice/event
```

> **NOTE:** An application can be also created using the CLI's interactive mode which you can start by running `vonage apps:create`

A file named `vonage_app.json` is created in your project directory and contains the newly created Vonage Application ID and the private key. A private key file named is also created.

Make a note of the Application ID that is echoed in your terminal when your application is created:

![screenshot of the terminal with Application ID underlined](/screenshots/tutorials/client-sdk/vonage-application-created.png)


> **NOTE:** Information about your application, including the Application ID, can also be found in the [Dashboard](https://dashboard.nexmo.com/voice/your-applications).