<p align="center">
<img width="400" valign="top" src="https://hydrogenshared.blob.core.windows.net/shared/hydrogen-logo.png" data-canonical-src="https://hydrogenshared.blob.core.windows.net/shared/hydrogen-logo.png" style="max-width:100%; ">
</p>
<br/>

# Hydrogen Astro JS SDK

Hydrogen AstroJS SDK allows you to accept payment using in your astro application

## Installation

Register for a merchant account on [Hydrogen Merchant Dashboard](https://dashboard.hydrogenpay.com) to get started.

```bash
npm install --save hydrogenpay-astro
```

```bash
yarn add hydrogenpay-astro
```

```bash
pnpm add hydrogenpay-astro
```

## Support

If you have any problems, questions or suggestions, create an issue here or send your inquiry to support@hydrogenpay.com

## Implementation

You should already have your api key, If not, go to [Profile & Settings](https://dashboard.hydrogenpay.com).

### Usage

```jsx
---
import HydrogenPayAstro from 'hydrogenpay-astro';
---

<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width" />
    <meta name="generator" content={Astro.generator} />
    <title>Astro</title>
  </head>
  <body>
    <h1>Astro</h1>
    <HydrogenPayAstro
      buttonText="Hydrogen Pay"
      amount={500}
      email="test@mail.com"
      customerName="John Doe"
      apiKey="PK_TEST_cca53e0b3bc7847aff94502b8a585f84"
      description="Test description"
      currency="NGN"
      frequency={1}
      isRecurring={false}
      endDate="2025-10-02"
      meta="ewr34we4w"
      transactionRef={`TRX_${Math.random().toString(36).substr(2, 10).toUpperCase()}`}
      metaData={[
        // { fieldName: "uniqueId", fieldDefaultValue: "DevStore14", fieldKey: "uniqueId", fieldType: 1 },
      ]}
    />
  </body>
  <script is:inline>
    window.onload = function () {
      window.onHydrogenPaySuccess = function (response, closeModal) {
        console.log(response);
        setTimeout(() => closeModal(), 3000);
      };
      window.onHydrogenPayClose = function (close) {
        console.log(close);
      };
    };
  </script>
</html>
```

## Options Type

| Name                 | Type       | Required | Desc                                                                        |
| -------------------- | ---------- | -------- | --------------------------------------------------------------------------- |
| currency             | `String`   | Required | The currency for the transaction e.g NGN, USD                               |
| email                | `String`   | Required | The email of the user to be charged                                         |
| description          | `String`   | Optional | The transaction description                                                 |
| customerName         | `String`   | Required | The fullname of the user to be charged                                      |
| amount               | `Number`   | Required | The transaction amount                                                      |
| apiKey               | `String`   | Required | Your LIVE or TEST apiKey or see above step to get yours                     |
| onHydrogenPaySuccess | `Function` | Optional | Callback when transaction is successful                                     |
| onHydrogenPayClose   | `Function` | Optional | Callback when transaction is closed of cancel                               |
| buttonText           | `String`   | Optional | Payment Button Text. Default: Hydrogen Pay                                  |
| isRecurring          | `bool`     | Optional | Recurring Payment                                                           |
| frequency            | `String`   | Optional | Recurring Payment frequency                                                 |
| endDate              | `String`   | Optional | Recurring Payment End Date. OPTIONAL but (REQUIRED when isRecurring = true) |
| transactionRef      | `String`   | Optional | Custom Transaction reference |
| metaData      | `Array`   | Optional | Transaction meta data |
