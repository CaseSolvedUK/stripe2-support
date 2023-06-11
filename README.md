# Stripe2 - Stripe payment integration for the frappe framework
#### Full set of Stripe payment methods, subscriptions and terminal support

## Features

* All Stripe <a href="https://stripe.com/docs/payments/payment-methods/overview" target="_blank">payment methods</a> supported including Cards, Wallets, Direct Debit, SEPA, Klarna and many more
* Website and card-present card reader payments (contact us for mobile bluetooth)
* ERPNext Payment Request support
* ERPNext (>14.16.0) Point-of-Sale integration (contact us for POSAwesome integration)
* One-off and recurring offline payments (subscriptions)
* Payments in <a href="https://stripe.com/docs/currencies" target="_blank">46 countries & 135+ currencies</a>
* Unlimited and free, just an additional 0.3% fee on top of standard <a href="https://stripe.com/pricing" target="_blank">Stripe fees</a>

**NOTE: currently must be used with ERPNext**

## Basic configuration of a Stripe account
1. Add a `Stripe2 Settings` document
2. Link to a completed Contact record of the person in your organisation responsible for external payment integrations, such as a Financial Director. This needs to be the Contact record of a valid system User with an email address
3. Link to the Company record that this payment integration is applicable to
4. Choose whether you want to take Live payments or only Test payments and submit
5. Verify the email address by clicking on the link in the email sent
6. Start the Stripe onboarding by clicking on `Connect with stripe`. You can set up a new Stripe account or link with an existing one
7. Once `Authorised` you only need to configure an Online and Offline Mode of Payment

## How to use the website checkout to take a payment
1. Submit a transaction compatible with a Payment Request. The most common would be a *Sales Invoice*
2. Create and submit a Payment Request for the transaction:
    1. ensure you use a Mode of Payment that *is not* the one configured for offline use
    2. run `set_payment_request_url()` on the Payment Request which will set the `payment_url` field
3. Copy and paste the contents of the `payment_url` field into a browser. A Stripe payment checkout page will be rendered
4. Choose your payment method, complete and submit the payment

Depending on the payment method, the payment will complete immediately or will be updated by webhook at a later time.

## How to set up a payment method for offline payments of subscriptions
As above, except the transaction should have a completed `auto_repeat` field.

## How to take offline subscription payments
1. Submit a transaction compatible with a Payment Request. The most common would be a *Sales Invoice*
2. Create a Payment Request for the transaction:
    1. ensure you use a Mode of Payment that *is* the one configured for offline use

Upon submission of the Payment Request, an offline payment will be attempted using the previously saved payment method.
If you completed the `To` email address in the payment request, an email will be sent with a pdf copy of the transaction attached upon completion of the payment.

## How to take Point of Sale Payments
This integration supports standalone Stripe card terminals like <a href="https://stripe.com/docs/terminal/readers/bbpos-wisepos-e" target="_blank">BBPOS WisePOS E</a> as well as browser payments. It also theoretically supports mobile bluetooth card readers but there is currently no existing mobile app available. Contact us if this is necessary for your scenario.

NOTE: you may need to contact Stripe to enable Terminal support on your account, <a href="https://stripe.com/docs/terminal/choosing-reader-and-integration#availability" target="_blank">please see this</a>.

1. Create a `POS Profile` with all the Payment Methods you intend to offer as Modes of Payment. This could include Browser Checkout, a Terminal Reader and Cash
2. If using a card reader, Assign a Location in `Stripe2 Settings`
3. Add a Terminal Mode of Payment and register the Pairing Code
4. Now Open Point of Sale and process a sale
5. Use the rendered buttons, like below, to take the payment:
![Screen Shot 2023-06-11 at 01 59 04](https://github.com/CaseSolvedUK/stripe2-support/assets/110036763/2edba316-4e36-4707-8961-df257f2b25a5)

## Support

[Discuss ideas in GitHub](https://github.com/CaseSolvedUK/stripe2-support/discussions)

[Report issues in GitHub](https://github.com/CaseSolvedUK/stripe2-support/issues)

#### License

Proprietary
