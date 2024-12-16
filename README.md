<!-- img src="./assets/ercaspay.png" alt="Ercaspay Logo" width="200" -->

![GitHub Header](https://github.com/user-attachments/assets/24c2a49a-393c-46d5-a7f1-0b4994b081a2)

**Ercaspay JavaScript SDK**. Built with ❣️ by Team Godspeed

# Table Of Content

- [Table Of Content](#table-of-content)
  - [Introduction 🚀](#introduction-)
    - [Why Did We Build This? 🤔](#why-did-we-build-this-)
    - [Ercaspay Js SDK Features 🚀](#ercaspay-js-sdk-features-)
  - [Installation 💽](#installation-)
  - [Usage 🚦](#usage-)
    - [SDK Typed Response](#sdk-typed-response)
    - [ErcaspayCheckout Class](#ercaspaycheckout-class)
      - [Example](#example)
      - [Example](#example-1)
  - [Initiates a Card Payment](#initiates-a-card-payment)
    - [Parameters](#parameters)
    - [Example](#example-2)
  - [Submit an OTP](#submit-an-otp)
    - [Parameters](#parameters-1)
    - [Resend an OTP](#resend-an-otp)
      - [Parameters](#parameters-2)
      - [Example](#example-3)
    - [Get Transaction Details](#get-transaction-details)
      - [Parameters](#parameters-3)
      - [Example](#example-4)
    - [Verify Transaction](#verify-transaction)
      - [Parameters](#parameters-4)
    - [Initiate a USSD Code Request](#initiate-a-ussd-code-request)
      - [Parameters](#parameters-5)
      - [Response](#response)
    - [Get Supported Bank List](#get-supported-bank-list)
      - [Parameters](#parameters-6)
      - [Response](#response-1)
    - [Cancel a USSD Transaction](#cancel-a-ussd-transaction)
      - [Parameters](#parameters-7)
      - [Response](#response-2)
    - [Initiate a Checkout Transaction](#initiate-a-checkout-transaction)
      - [Parameters](#parameters-8)
      - [Response](#response-3)
      - [Response](#response-4)
    - [Verify a Checkout Transaction](#verify-a-checkout-transaction)
  - [Parameters](#parameters-9)
  - [Response](#response-5)
  - [Example](#example-5)

## Introduction 🚀

Introducing the **Ercaspay** JavaScript SDK: A Hackathon Innovation in Payment Solutions! 💡🏆

Built during an exciting hackathon sprint, our SDK is crafted on top of the powerful Ercaspay APIs to help developers easily integrate payment solutions into their apps. We’ve designed it to be intuitive, efficient, and super easy to use—no more complex setups or long implementation times. With our SDK, you’ll have everything you need to implement payments smoothly and get back to focusing on what matters most—building amazing products. 🚀

### Why Did We Build This? 🤔

During the hackathon, we saw a common challenge developers face: the complexity of integrating payment gateways. Having worked with payment APIs before, I know how frustrating it can be when there’s no SDK, leaving you to manually test the APIs with tools like Postman just to figure out what responses to expect. And even when an SDK exists, many don’t offer proper typing, making it a guessing game when calling methods or properties.

That’s why we built this SDK—to solve all of these problems. But we didn’t stop there. We went the extra mile to ensure it’s not just functional but robust and easy to use. We battle-tested our **SDK** with over **70** test suites to ensure reliability and performance under real-world conditions. We also added comprehensive documentation to each and every method and property, so users can start integrating right away—without having to read the docs. As you call a method or access a property, you’ll see all the details you need right in your **IDE**, making it easier than ever to integrate Ercaspay into your projects.

### Ercaspay Js SDK Features 🚀

Why should you use the **Ercaspay JS SDK** 🤔 ?

- **Effortless Integration:** The Ercaspay JS SDK streamlines the integration process, allowing users to interact with the Ercaspay Payment APIs without the usual hassle. Gone are the days of testing APIs manually in tools like Postman—we’ve made it as easy as calling a method.

- **Accelerated Development:** With simplified methods, clear type definitions, and enhanced autocompletion, developers can ship their products faster and reduce time-to-market. We’ve taken the guesswork out of the equation, helping you focus more on building and less on debugging.

- **Minimal API Interaction:** Achieve robust payment functionalities with minimal direct interaction with the APIs. Our SDK abstracts away the complexity, so you can integrate payment features without getting bogged down by API details.

- **Typed Responses:** Automatic type definitions for API responses ensure your code is both robust and error-free. Responses are now typed out of the box, giving developers a more structured and predictable development experience.

- **TypeScript / JavaScript Autocompletion:** Whether you're working in TypeScript or JavaScript, our SDK supports autocompletion, making it easier to develop by providing accurate method suggestions and reducing errors. This feature significantly boosts productivity and helps you write more reliable code.

- **Comprehensive JSDoc Support:** Say goodbye to searching for documentation. Our SDK comes with thorough JSDoc support, giving you all the descriptive and actionable information you need right in your IDE, so you can focus on what really matters—building your app.

- **Efficient Error Handling:** Error handling is a breeze with the Ercaspay JS SDK. It provides clear, detailed error messages, making it easier for developers to troubleshoot and resolve issues quickly, ensuring a smoother integration.

These enhancements aim to provide developers with a more powerful, flexible, and enjoyable experience when integrating [Ercaspay Payment APIs](https://ercaspay.com/) into their applications.

## Installation 💽

To install the **SDK** in your application, you can install using `npm, yarn, pnpm or bun`

**Npm**

```bash

npm install ercaspay-sdk

```

**Yarn**

```bash
yarn add ercaspay-sdk

```

**Bun**

```bash
bun add ercaspay-sdk

```

## Usage 🚦

While the Ercaspay JS SDK is designed to be intuitive and easy to use (so you can start integrating without even opening the docs!), I’ll still walk you through each key SDK method to make sure you’re equipped with all the details.

To get started with the Ercaspay JS SDK, you first need to import the ErcaspayClient from the `ercaspay-sdk` package. This class is your gateway to the SDK, providing all the methods you need to interact with the Ercaspay Payment APIs.

```typescript
import { ErcaspayClient } from "ercaspay-sdk";
```

Then we create a new instance of the **ErcaspayClient** which allows us to interact with the the methods in the **ErcaspayClient**. It takes 2 arguments.

1. The Ercaspay Secret Key
2. The Environment. (Optional, defaults to `development`)

The Secret Key can be gotten from the **Ercaspay** website. <https://sandbox.ercaspay.com/sign-up> or <https://merchant.ercaspay.com/sign-up>

```typescript
const ercaspay = new ErcaspayClient(
  process.env.ERCASPAY_SECRET_KEY as string,
  process.env.NODE_ENV as string
);
```

### SDK Typed Response

The **SDK** provides **typed responses** for every method call, ensuring that you get consistent and structured data with every interaction. The base response object contains key information, including the request status, response code, error message or response message (if applicable), and the actual data returned from the API. With clear response data, you can tailor your application’s behavior based on the success or failure of an operation—allowing you to respond appropriately and handle errors efficiently.

```typescript
/**
 * Represents a base response structure for API requests.
 * @template TResponse - The type of the response body.
 */
export interface IBaseResponse<TResponse> {
  /**
   * Indicates whether the request was successful.
   * @type {boolean}
   */
  requestSuccessful: boolean;

  /**
   * A code representing the status of the response (e.g., success, error).
   * @type {string}
   */
  responseCode: string;

  /**
   * A message providing additional details on the response, typically used for errors.
   * @type {string}
   */
  errorMessage?: string;

  /**
   * A message providing additional details on the response, typically used for success response.
   * @type {string}
   */
  responseMessage?: string;

  /**
   * The actual data returned in the response.
   * @type {TResponse}
   */
  responseBody: TResponse;
}
```

Let’s assume you’re initiating a payment using the `checkout.initiateTransaction` method. When you call this method, it returns a typed response that you can directly assign to a variable. This response includes crucial details, such as the success status, response message, and any additional data returned by the API.

```typescript
import { ErcaspayClient } from "ercaspay-sdk";

const ercaspay = new ErcaspayClient(
  process.env.ERCASPAY_SECRET_KEY as string,
  process.env.NODE_ENV as string
);

const response = await ercaspay.checkout.initiateTransaction({
  amount: 10000,
  paymentReference: "R5md7gd9b4s3h2j5d67g",
  paymentMethods: "card,bank-transfer,ussd,qrcode",
  customerName: "Adedoyin Emmanuel",
  customerEmail: "hi@adedoyinemmanuel.dev",
  customerPhoneNumber: "09061626364",
  redirectUrl: "https://github.com/adedoyin-emmanuel",
  description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
  currency: "NGN",
  feeBearer: "customer",
  metadata: {
    firstname: "Temi",
    lastname: "Girl",
    email: "temigirl@mail.com",
  },
});

// check if the response was successful, if not, return a response to the client.

if (!response.requestSuccessful)
  return res.status(response.status).json({ message: response.message });

// Response was successful, I can now get the checkout_url

const checkoutUrl = response.responseBody.checkoutUrl;

// redirect the client to the checkout_url

res.redirect(checkoutUrl); // assuming you are using express JS
```

### ErcaspayCheckout Class

The `ErcaspayCheckout` class is part of the Ercaspay JS SDK and provides methods to handle transactions related to the ErcasPay Checkout platform. It allows you to initiate a transaction and verify the status of a transaction using its reference.

**Methods**

1. `initiateTransaction`: Initiates a checkout transaction on the ErcasPay platform. The method first validates the input data using a predefined schema, and then it sends a request to initiate the transaction.

#### Example

```typescript
const response = await client.checkout.initiateTransaction({
  amount: 10000,
  paymentReference: "R5md7gd9b4s3h2j5d67g",
  paymentMethods: "card,bank-transfer,ussd,qrcode",
  customerName: "Adedoyin Emmanuel",
  customerEmail: "hi@adedoyinemmanuel.dev",
  customerPhoneNumber: "09061626364",
  redirectUrl: "https://github.com/adedoyin-emmanuel",
  description: "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
  currency: "NGN",
  feeBearer: "customer",
  metadata: {
    firstname: "Temi",
    lastname: "Girl",
    email: "temigirl@mail.com",
  },
});
```

As you know, the SDK comes with `Typed Responses` which means automatic type definitions for API responses. Below is an example of what the `initiateTransaction` method returns.

```typescript
/**
 * The unique payment reference.
 * @type {string}
 */
paymentReference: string;

/**
 * A unique transaction reference.
 * @type {string}
 */
transactionReference: string;

/**
 * The URL to complete the checkout process.
 * @type {string}
 */
checkoutUrl: string;
```

2. `verifyTransaction`: Verifies the status of a checkout transaction using its unique reference. This is useful for checking if a transaction has been successfully completed.

#### Example

```typescript
const validTransactionRef = "ERCS|20241214214035|1734208835283";

const response = await client.checkout.verifyTransaction(validTransactionRef);
```

**Typed Response**

```typescript
/**
 * Represents the response structure for verifying a checkout transaction.
 */
export interface IVerifyCheckoutTransactionResponse {
  /**
   * The domain where the transaction was processed.
   * @type {string}
   */
  domain: string;

  /**
   * The status of the transaction (e.g., success, failed).
   * @type {string}
   */
  status: string;

  /**
   * The ERCs reference associated with the transaction.
   * @type {string}
   */
  ercs_reference: string;

  /**
   * The unique transaction reference.
   * @type {string}
   */
  tx_reference: string;

  /**
   * The amount for the transaction.
   * @type {number}
   */
  amount: number;

  /**
   * A description of the transaction.
   * @type {string}
   */
  description: string;

  /**
   * The timestamp when the payment was made.
   * @type {string}
   */
  paid_at: string;

  /**
   * The timestamp when the transaction was created.
   * @type {string}
   */
  created_at: string;

  /**
   * The payment channel used for the transaction.
   * @type {string}
   */
  channel: string;

  /**
   * The currency in which the transaction was processed.
   * @type {string}
   */
  currency: string;

  /**
   * Additional metadata related to the transaction (optional).
   * @type {Record<string, any> | undefined}
   */
  metadata?: Record<string, any>;

  /**
   * The fee charged for processing the transaction.
   * @type {number}
   */
  fee: number;

  /**
   * Specifies who bears the transaction fee ("customer" or "merchant").
   * @type {string}
   */
  fee_bearer: string;

  /**
   * The amount that was actually settled for the transaction.
   * @type {number}
   */
  settled_amount: number;

  /**
   * Information about the customer involved in the transaction.
   * @type {ICustomer}
   */
  customer: ICustomer;
}

/**
 * Represents the details of a customer.
 */
export interface ICustomer {
  /**
   * The name of the customer.
   * @type {string}
   */
  name: string;

  /**
   * The email address of the customer.
   * @type {string}
   */
  email: string;

  /**
   * The phone number of the customer (optional).
   * @type {string | undefined}
   */
  phone_number?: string;

  /**
   * A unique reference identifier for the customer.
   * @type {string}
   */
  reference: string;
}
```

## Initiates a Card Payment

Initializes a payment process by sending required payment details, device information, and a transaction reference.

#### Parameters

- `data(Object)`: Data for initiating the payment.
  - `payload` (Number): Base64-encoded payment details containing sensitive card information.
  - `transactionReference` (String): A unique identifier for the transaction.
  - `deviceDetails ` (Object): Information about the user's device for 3D Secure validation.

#### Example

```typescript
const response = await ercaspayCard.initiatePayment({
  payload: "base64-encoded-payment-details",
  transactionReference: "txn_123456789",
  deviceDetails: {
    payerDeviceDto: {
      device: {
        browser: "Chrome",
        browserDetails: {
          "3DSecureChallengeWindowSize": "03",
          acceptHeaders: "application/json",
          colorDepth: 24,
          javaEnabled: true,
          language: "en-US",
          screenHeight: 1080,
          screenWidth: 1920,
          timeZone: -60,
        },
        ipAddress: "192.168.1.1",
      },
    },
  },
});
```

## Submit an OTP

Authenticates a transaction by submitting the OTP sent to the customer.

#### Parameters

- `data(Object)`: Data for Submitting Otp.

  - `otp` (String): The one-time password received by the customer.
  - `gatewayReference` (Object): A unique reference returned during payment initialization.
  - `transactionReference` (Object):A unique identifier for the transaction.

-

```typescript
const response = await ercaspayCard.submitOTP({
  otp: "123456",
  gatewayReference: "gw_123456",
  transactionReference: "txn_123456789",
});
```

### Resend an OTP

Requests a new OTP for a transaction when the initial OTP is not received or has expired.

#### Parameters

- `data(Object)`: Data for resending the OTP.

  - `gatewayReference` (Object): A unique reference returned during payment initialization.
  - `transactionReference` (Object):A unique identifier for the transaction.

#### Example

```typescript
const response = await ercaspayCard.resendOTP({
  gatewayReference: "gw_123456",
  transactionReference: "txn_123456789",
});
```

### Get Transaction Details

Retrieves information about a specific transaction using its reference.

#### Parameters

- `transactionReference` (Object):A unique identifier for the transaction.

#### Example

```typescript
const response = await ercaspayCard.getDetails("txn_123456789");
```

### Verify Transaction

Checks the status of a transaction to ensure it has been successfully completed.

#### Parameters

- `reference` (String): A unique identifier for the transaction.

```typescript
const response = await ercaspayCard.verifyTransaction("txn_123456789");
```

### Initiate a USSD Code Request

Generates a USSD code for making payments by providing transaction details and the bank name.

#### Parameters

- `data(Object)`: Data for generating the USSD code.

  - `transactionReference` (Object): A unique reference returned during payment initialization.
  - `amount` (Number):The transaction amount.
  - `bankName` (String):The name of the bank selected for payment.

#### Response

The response includes the following fields:

- `status` (String): The status of the operation (e.g., "success").
- `gatewayMessage` (String): Message from the payment gateway.
- `transactionReference` (String): The reference for the initiated transaction.
- `gatewayReference` (String): A unique reference returned by the payment gateway.
- `ussdCode` (String): The generated USSD code for the transaction.
- `paymentCode` (String): A unique payment code associated with the transaction.
- `amount` (Number): The transaction amount.

```typescript
const response = await ercaspayUSSD.initiateCode({
  transactionReference: "txn_123456789",
  amount: 10000,
  bankName: "First Bank",
});
```

### Get Supported Bank List

Retrieves the list of banks supported for USSD transactions.

#### Parameters

None

#### Response

An array of strings representing the names of the supported banks.

```typescript
const response = await ercaspayUSSD.getBankList();
console.log(response.data); // ["First Bank", "GTBank", "Access Bank", ...]
```

### Cancel a USSD Transaction

Cancels an ongoing USSD transaction using its reference.

#### Parameters

- `transactionReference` (Object): The unique identifier for the transaction to be canceled.

#### Response

The response may include details about the cancellation status, such as:

- `status` (String): Indicates whether the transaction was successfully canceled.
- `gatewayMessage` (String): Message from the payment gateway regarding the cancellation.
- `transactionReference` (String): The reference of the transaction being canceled.

```typescript
const response = await ercaspayUSSD.cancel("txn_123456789");
console.log(response.data);
```

### Initiate a Checkout Transaction

Initiates a checkout transaction by providing payment details, customer information, and optional metadata.

#### Parameters

- `data` (Object): Details of the transaction.
  - `amount` (Number): The transaction amount.
  - `paymentReference` (String): A unique identifier for the payment.
  - `paymentMethods` (String): Accepted payment methods (e.g., "card", "bank").
  - `customerName` (String): The full name of the customer.
  - `customerEmail` (String): The email address of the customer.
  - `customerPhoneNumber` (String, optional): The phone number of the customer.
  - `currency` (String): The transaction currency (e.g., "NGN", "USD").
  - `feeBearer` (String, optional): Indicates who bears the transaction fee (`"customer"` or `"merchant"`).
  - `redirectUrl` (String, optional): The URL to redirect the user after payment.
  - `description` (String, optional): A brief description of the transaction.
  - `metadata` (Object, optional): Additional data related to the transaction.

#### Response

The response includes the following fields:

- `paymentReference` (String): The unique identifier for the payment.
- `transactionReference` (String): The unique identifier for the transaction.
- `checkoutUrl` (String): The URL to complete the payment process.

#### Response

The response includes the following fields:

```typescript
const response = await ercaspayCheckout.initiateTransaction({
  amount: 5000,
  paymentReference: "pay_123456789",
  paymentMethods: "card",
  customerName: "John Doe",
  customerEmail: "johndoe@example.com",
  customerPhoneNumber: "2348012345678",
  currency: "NGN",
  feeBearer: "customer",
  redirectUrl: "https://example.com/redirect",
  description: "Payment for product ABC",
  metadata: { orderId: "ORD12345" },
});

console.log(response.data.checkoutUrl);
```

### Verify a Checkout Transaction

Verifies the status of a checkout transaction using its transaction reference.

## Parameters

- `transactionReference` (String): The unique identifier for the transaction to be verified.

## Response

The response includes details about the transaction:

- `domain` (String): The transaction domain.
- `status` (String): The status of the transaction (e.g., "success", "failed").
- `ercs_reference` (String): The unique reference returned by the payment gateway.
- `tx_reference` (String): The transaction reference.
- `amount` (Number): The transaction amount.
- `description` (String): A brief description of the transaction.
- `paid_at` (String): The timestamp when the payment was completed.
- `created_at` (String): The timestamp when the transaction was initiated.
- `channel` (String): The payment channel used (e.g., "card", "bank").
- `currency` (String): The transaction currency.
- `metadata` (Object, optional): Additional data related to the transaction.
- `fee` (Number): The transaction fee.
- `fee_bearer` (String): Who bears the transaction fee ("customer" or "merchant").
- `settled_amount` (Number): The amount settled after deducting fees.
- `customer` (Object): Customer details.
  - `name` (String): The customer's full name.
  - `email` (String): The customer's email address.
  - `phone_number` (String, optional): The customer's phone number.
  - `reference` (String): A unique reference for the customer.

## Example

```typescript
const response = await ercaspayCheckout.verifyTransaction("txn_987654321");

console.log(response.data.status); // "success"
console.log(response.data.customer.name); // "John Doe"
```
