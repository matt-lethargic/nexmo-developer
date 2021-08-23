---
title: Install the Vonage CLI Beta
description: Install the Vonage CLI Beta to get the latest functionality
---

The Vonage CLI allows you to carry out many operations on the command line. Examples include creating applications, purchasing numbers, and linking a number to an application.

To install the Beta version of the CLI with NPM you can use:

``` shell
npm install @vonage/cli@beta -g
```

Set up the Nexmo CLI to use your Vonage API Key and API Secret. You can get these from the [settings page](https://dashboard.nexmo.com/settings) in the Dashboard.

Run the following command in a terminal, while replacing `API_KEY` and `API_SECRET` with your own:

```bash
vonage config:set --apiKey=API_KEY --apiSecret=API_SECRET
```