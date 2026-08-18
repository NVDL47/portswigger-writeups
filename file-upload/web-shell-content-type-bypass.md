# Web Shell Upload via Content-Type Restriction Bypass

## Vulnerability

Insufficient file-upload validation allowing a server-side script to be uploaded and executed.

## How I Found It

I opened the lab and went to my account page, where I found an option to upload an account image.

I tested the file-upload functionality using a PHP file with a `.jpg.php` filename. The file contained a PHP command-execution payload that I had previously created while working through a similar lab.

I uploaded the file and opened it in a new tab.

## What Worked

The uploaded PHP file was accessible and executed on the server.

I used the URL parameter provided by the payload to execute commands remotely. I then used:

`cat /home/carlos/secret`

to read the secret file.

I copied the resulting value and submitted it to complete the lab.

## What I'd Check Next Time

For file-upload functionality, I would investigate how the application validates filenames, extensions, MIME types, and file contents.

I would also check whether uploaded files are stored in a location where server-side code can be executed.
