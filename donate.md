---
layout: page
title: Donate to the Iris Music Project
permalink: /donate/
---

Thank you so much for supporting the Iris Music Project!

## Become a monthly supporter

Please visit our Patreon website to become a monthly supporter of the Iris Music Project: [patreon.com/irismusicproject](https://www.patreon.com/irismusicproject)

## One-time donations

All donations are tax deductible.  There are two simple ways to donate:

1. Make check out to “Iris Music Project” and mail to:  

   ​		Iris Music Project  
   ​		9607 Rocksparkle Row  
   ​		Columbia MD 21045

2. [Donate via credit card](https://irismusicproject.github.io/stripe.html)
3. [Donate via Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=J5D5F8NWDLK6W&source=url)

<!-- Load Stripe.js on your website. -->
<script src="https://js.stripe.com/v3"></script>

<!-- Create a button that your customers click to complete their purchase. Customize the styling to suit your branding. -->
<button
  style="background-color:#6772E5;color:#FFF;padding:8px 12px;border:0;border-radius:4px;font-size:1em"
  id="checkout-button-price_1H5NgPDFx8DILfCPJgxI9y6N"
  role="link"
  type="button"
>
  Checkout
</button>

<div id="error-message"></div>

<script>
(function() {
  var stripe = Stripe('pk_live_BorxXvQDTFJZuy7wN1QUG5Gg00mtbHjpei');

  var checkoutButton = document.getElementById('checkout-button-price_1H5NgPDFx8DILfCPJgxI9y6N');
  checkoutButton.addEventListener('click', function () {
    // When the customer clicks on the button, redirect
    // them to Checkout.
    stripe.redirectToCheckout({
      lineItems: [{price: 'price_1H5NgPDFx8DILfCPJgxI9y6N', quantity: 1}],
      mode: 'payment',
      // Do not rely on the redirect to the successUrl for fulfilling
      // purchases, customers may not always reach the success_url after
      // a successful payment.
      // Instead use one of the strategies described in
      // https://stripe.com/docs/payments/checkout/fulfillment
      successUrl: 'https://irismusicproject.github.io/success.html',
      cancelUrl: 'https://irismusicproject.github.io/canceled.html',
    })
    .then(function (result) {
      if (result.error) {
        // If `redirectToCheckout` fails due to a browser or network
        // error, display the localized error message to your customer.
        var displayError = document.getElementById('error-message');
        displayError.textContent = result.error.message;
      }
    });
  });
})();
</script>
