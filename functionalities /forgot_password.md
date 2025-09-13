# 1. Rate Limiting 

1. **Capture Reset Request**
   - Open your browser and send a password reset request.

2. **Test Multiple Requests Manually**
   - Send the same request multiple times quickly in Repeater.

3. **Automated Testing with Burp Intruder**
   - If you don't see any signs of blocking, send the request to Burp Intruder with the same email as the payload. Set it to make 50–100 requests.

4. **Analyze Responses**
   - Look for status codes like:
     - `429 Too Many Requests`
     - Any other unusual behavior indicating rate limiting or throttling.

5. **Optional: Spoof Headers**
   - Try adding or spoofing headers to bypass simple IP-based rate limiting:
   ```http
   X-Forwarded-For: 127.0.0.1

# 2. No Link Expiration or Token Reuse

## Good Implementation Practices

Reset tokens should expire after:

- One successful password change
- A short duration (typically **10–30 minutes**)

---

## How to Test Using Burp Suite

### 1. Obtain the Reset Link
- Use a temporary inbox service or your own account.
- A typical password reset link looks like:

```text
https://target.com/reset-password?token=abcd1234
