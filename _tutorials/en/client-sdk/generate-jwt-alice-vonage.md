---
title: Generate a JWT
description: In this step you learn how to generate a valid JWT for your Client SDK Application.
---

# Generate a JWT

The Client SDK uses [JWTs](/concepts/guides/authentication#json-web-tokens-jwt) for authentication. The JWT identifies the user name, the associated application ID and the permissions granted to the user. It is signed using your private key to prove that it is a valid token.

Run the following commands, remember to replace the `APPLICATION_ID` variable with id of your application and `PRIVATE_KEY` with the name of your private key file.

> **NOTE:** To quickly get your application id you can run the Vonage CLI command, `vonage apps`, to view a list of your applications.

``` shell
vonage jwt --app_id=APPLICATION_ID --subject=Alice --key_file=./PRIVATE_KEY --acl='{"paths":{"/*/users/**":{},"/*/conversations/**":{},"/*/sessions/**":{},"/*/devices/**":{},"/*/image/**":{},"/*/media/**":{},"/*/applications/**":{},"/*/push/**":{},"/*/knocking/**":{},"/*/legs/**":{}}}'
```

The above commands set the expiry of the JWT to one day from now, which is the maximum.

Make a note of the JWT you generated:

![terminal screenshot of a generated sample JWT](/screenshots/tutorials/client-sdk/generated-jwt-key-vonage.png)

## Further information

* [online JWT generator](/jwt)
* [JWT guide](/concepts/guides/authentication#json-web-tokens-jwt)
