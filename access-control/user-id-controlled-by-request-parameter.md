# User ID Controlled by Request Parameter

## Vulnerability

Broken access control allowing access to another user's account.

## How I Found It

I opened the lab and looked through the posts until I found one written by Carlos. I clicked on his username and noticed that his user ID was included in the URL.

I copied Carlos's user ID and then logged into my own account using the supplied credentials.

## What Worked

I changed the user ID parameter in my account URL to Carlos's user ID.

Instead of preventing access, the application displayed Carlos's account page.

The page contained an API key, which I copied and submitted to complete the lab.

## What I'd Check Next Time

Whenever an application uses an identifier in a URL or request to select a user or other resource, I would test whether changing that identifier allows access to another user's data.

I would also check whether the server verifies that the authenticated user is authorized to access the requested resource.
