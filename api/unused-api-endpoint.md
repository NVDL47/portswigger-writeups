# Finding and Exploiting an Unused API Endpoint

## Vulnerability

Improperly exposed API functionality allowing an authenticated user to modify a product.

## How I Found It

I opened the lab in Firefox with Burp Suite running and intercepted a request made when viewing a product. I sent the request to Burp Repeater and changed the HTTP method from `GET` to `OPTIONS`.

The response showed that the endpoint allowed both `GET` and `PATCH` requests.

I tried sending a `PATCH` request, but initially received an authorization error. I then logged into the supplied user account and sent the request again.

## What Worked

After authenticating, the `PATCH` request was accepted but returned an error indicating that the content type was incorrect.

I changed the `Content-Type` to `application/json` and added a JSON body setting the product price to `0`.

The server returned a `200 OK` response. After refreshing the product page, the price had been changed to `0`.

I then increased the quantity to seven and placed an order, completing the lab.

## What I'd Check Next Time

When an endpoint responds to an `OPTIONS` request, I would check which HTTP methods are allowed and investigate methods such as `PATCH` that may expose functionality not available through the normal application interface.

I would also test whether authentication and authorization are properly enforced for those methods.
