##1. Rate Limiting
-Send a reset request in the browser and capture it in Burp Repeater.
-Send the same request multiple times quickly.
-If you don't see any signs of blocking, send the request to Burp Intruder with the same email as the payload. Set it to make 50–100 requests.
-Check responses in the Intruder results tab. Do you get a 429 Too Many Requests Or something different after a point?
-Try adding or spoofing headers like:

X-Forwarded-For: 127.0.0.1
