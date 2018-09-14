# Vipps PSP API

API version: 2.

Document version 0.1.0.

_**IMPORTANT:**_ This document is a work in progress.

# About this API

Vipps Netthandel (eCommerce) via PSP offers functionality for payments on
websites and apps (P2M). Vipps Netthandel offer merchants functionality to
provide a solution where the consumer only enters her Norwegian mobile number
to retrieve a payment request in Vipps app.

In the Vipps app the consumer
selects a payment source to complete the payment request. Vipps initiates
the payment transaction on the selected source and provide feedback to the
PSP of the payment card selected.

The PSP processes the payment transaction
and provides feedback to merchant and Vipps of the payment transaction
success or failure.

# Differences from PSP API version 1

* Added support for redirection of user after payment completion in Vipps app
* Added support for providing the makePayment-URL in the initiate payment call
* Improved authorization of the makePayment call by adding the authorization header value
* Improved and more consistent parameter names in the API

# External documentation

## Technical details about the API

Swagger/OAS API documentation is available on GitHub: https://github.com/vippsas/vipps-psp-api

## Getting access to the Vipps Developer Portal

See the
[Vipps Developer Portal Getting Started](https://github.com/vippsas/vipps-developers/blob/master/vipps-developer-portal-getting-started.md)
guide general information about the Vipps Developer Portal.
This is where you create keys to the API.

# Payment sequence

![PSP API sequence diagram](images/psp-sequence-diagram.png)

## Initiate payment

Payment request is initiated by PSP to Vipps API after end user has request to pay with VIpps. Vipps creates the payment and returns a link to Vipps landing page where end user can confirm the mobile number. Once user has confirmed number the payment can be considered initiated.

## Payment confirmation

After payment initiation, Vipps sends push notification or redirects user to Vipps app. End user verifies the Vipps profil bu login in to Vipps app. In Vipps app the end user can select payment source and confirm the amount.

## MakePayment

Once the end user has confirmed the payment, Vipps shares the encrypted card details with the PSP to the makePaymentUrl. PSP tries to process the payment through the acquirer and responds to the makePayment-call with the payment request status. End user receives confirmation in Vipps app. Vipps redirects the end user to the redirectUrl provided during payment initiation.

## StatusUpdates

To provide a consistent end user experience it is important that Vipps is notified by changes to the payment status when it is captured, cancelled or refunded. Vipps also provides an endpoint to check the payment status.

# Questions or comments?

Please use GitHub's built-in functionality for
[issues](https://github.com/vippsas/vipps-invoice-api/issues) and
[pull requests](https://github.com/vippsas/vipps-invoice-api/pulls),
or [contact us](https://github.com/vippsas/vipps-developers/blob/master/contact.md).
