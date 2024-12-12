![](/assets/ercaspay.png)


**Ercaspay JavaScript SDK**. Built with ❣️ by Team Goodspeed

# Table Of Content


- [Table Of Content](#table-of-content)
  - [Introduction 🚀](#introduction-)
    - [Why Did We Build This? 🤔](#why-did-we-build-this-)
    - [Ercaspay Js SDK Features 🚀](#ercaspay-js-sdk-features-)
  - [Installation 💽](#installation-)
  - [Usage 🚦](#usage-)


## Introduction 🚀

Introducing the **Ercaspay** JavaScript SDK: A Hackathon Innovation in Payment Solutions! 💡🏆
Built during an intense hackathon sprint, this SDK revolutionizes payment integration for developers, offering a streamlined, chainable interface that simplifies how applications connect with **Ercaspay** payment ecosystem. Crafted with passion and innovation by Team Godspeed.

### Why Did We Build This? 🤔

During the hackathon, We discovered developers struggling with complex payment gateway integrations. This SDK is our solution - a game-changing tool that simplifies financial technologies.

Motivated by more than just winning, I was deeply impressed by **Ercaspay**  innovative approach. This project became an opportunity to showcase how technology can transform payment integrations, demonstrating our team's technical prowess and creative problem-solving.

The SDK represents our commitment to pushing boundaries in developer tools. Since the hackathon, I've been passionate about sharing this approach, highlighting how innovative solutions can revolutionize payment technology integration.

### Ercaspay Js SDK Features 🚀

Why should you use the **Ercaspay JS SDK** 🤔 ?

- **Effortless Integration:** The Ercaspay Js SDK streamlines the integration process, allowing users to interact with Ercaspay Payment APIs seamlessly.

- **Accelerated Development:** With simplified methods and enhanced autocompletion, developers can ship their products faster, reducing time-to-market.

- **Minimal API Interaction:** Users can achieve robust payment functionalities without directly interacting with the Ercaspay Payment APIs, making development more straightforward.

- **Typed Responses:** The Ercaspay Js SDK provides automatic type definitions for API responses, ensuring robust and error-free code. Now, responses are effortlessly typed, offering developers a more structured development experience.

- **TypeScript / JavaScript Autocompletion:** Leverage TypeScript / JavaScript autocompletion for a smoother development process. The SDK seamlessly integrates with TypeScript, enhancing developer productivity by providing accurate suggestions and reducing errors. This also works with JavaScript.

- **Comprehensive JSDoc Support:** Enjoy thorough JSDoc support that enhances code documentation. Developers can benefit from descriptive and comprehensive information right at their fingertips, making it easier to understand and utilize the SDK's capabilities.

- **Efficient Error Handling:** The SDK facilitates efficient error handling, providing detailed information for better debugging. Developers can easily identify and resolve issues, ensuring a more reliable integration.

- **Intuitive Webhook Management:** Manage webhook transactions effortlessly. The SDK introduces clear methods for retrieving and deleting webhook error logs, ensuring a smooth and error-free webhook integration.

These enhancements aim to provide developers with a more powerful, flexible, and enjoyable experience when integrating [Ercaspay Payment APIs](https://ercaspay.com/) into their applications.

## Installation 💽

To install the **SDK** in your application, you can install using `npm, yarn, pnpm or bun`

**Npm**

```bash

npm install @ercaspay/js

```

**Yarn**

```bash
yarn add @ercaspay/js

```

**Bun**

```bash
bun add @ercaspay/js

```


## Usage 🚦

Though **Ercaspay Js SDK** provides easy methods that can be used even without reading documentation, I will still do my best to explain each **SDK** method. To use the **Ercaspay JS SDK**. You've to import the **ErcaspayClient** from the **@ercaspay/js** package. That class provides the interface to work with the **SDK**.

```typescript
import ErcaspayClient from "@ercaspay/js";
```

Then we create a new instance of the **ErcaspayClient** which allows us to interact with the the methods in the **ErcaspayClient**. It takes 3 arguments.

1. The Ercaspay Public Key
2. The Ercaspay Private Key
3. The Environment.

The Public and Private Key can be gotten from the **Ercaspay** website. <https://sandbox.ercaspay.com/sign-up> or <https://merchant.ercaspay.com/sign-up>

```typescript
const ercaspay = new ErcaspayClient(
  process.env.ERCASPAY_PUBLIC_KEY as string,
  process.env.ERCASPAY_PRIVATE_KEY as string,
  process.env.NODE_ENV as string
);
```
