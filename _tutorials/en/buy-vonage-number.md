---
title: Buy a Vonage number
description: In this step you learn how to purchase a Vonage number.
---

# Buy a Vonage number 

## Using the Dashboard

First you can browse [your existing numbers](https://dashboard.nexmo.com/your-numbers).

If you have no spare numbers you can [buy one](https://dashboard.nexmo.com/buy-numbers).

## Using the Vonage CLI

You can purchase a number using the Vonage CLI. The following commands purchases an available number in the US. Specify [an alternate two-character country code](https://www.iban.com/country-codes) to purchase a number in another country.

Search for a number that has voice features:

```
vonage numbers:search US --type=mobile-lvn
```

Buy the number, replacing `NUMBER` with the number from the previous step

```
vonage numbers:buy NUMBER US
```

Make a note of the number returned, as you'll need it later.
