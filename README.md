# paypal-integration-with-wappler
An example of how to integrate PayPal payment with Wappler

# Basic Concept/Workflow
Step 0 [Client-side]: Setup UI for payment. Use the sample frontend HTML code in index.ejs.

Step 1 [Server-side]: create order API: You first generate Access Token using the client ID and secrete.
The endpoint for sandbox account is https://api-m.sandbox.paypal.com/v1/oauth2/token. The create order API will use the access token obtained from the first action to generate an Order ID. This Order ID is returned to the front-end to for the payer to use to approve the order.

Step 2 [Client Side]: The Javascript client code will use the order ID returned by the create order API to allow the payer to login to Paypal and approve payment. Once the payer approves the payment, the Javascript client code will again send a request to the capture order API on the server to finalize the transaction.

Step 3 [Server-side]: capture order API: the capture order API uses the Order ID to capture payment and store order information. https://api-m.sandbox.paypal.com/v2/checkout/orders/ORDER_ID_HERE/capture

# Reference
 Integrate PayPal Checkout for online payments, https://developer.paypal.com/docs/checkout/standard/integrate/
