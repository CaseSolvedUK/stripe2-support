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

**Many of the following guides assume you are using this Stripe Integration with ERPNext:**

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

## How to use the integration in the frappe framework without ERPNext


## Support

[Discuss ideas in GitHub](https://github.com/CaseSolvedUK/stripe2-support/discussions)

[Report issues in GitHub](https://github.com/CaseSolvedUK/stripe2-support/issues)

#### License

Proprietary
