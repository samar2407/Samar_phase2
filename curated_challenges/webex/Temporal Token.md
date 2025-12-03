# Temporal Token
This challenge asks us to find the flag by manipulating the jwt token in the website as we were not able to login to the website because the token was already expired.
# Working
We first do inspect element and examine the cookie value. We identify that it is JSON Web Token as the value is divided into three parts with dots separating the header, payload and signature. We then use Burp > Proxy > HTTP History and find a request to /api/flag with our token value at cookie header. We find out using JWT.io that our token's exp value is 0, which means the token is getting expired so we cannot login.

<img width="1920" height="1020" alt="Screenshot (41)" src="https://github.com/user-attachments/assets/4048462d-2d6b-47a4-bb49-f4b111e48bac" />

We then change our token's exp value to a timestamp which will be valid in the future, and use it's base64 converted form as the payload. We also change the algorithm to "none" so that it doesnt check the signature. We then fully convert the cookie value with a valid future timestamp and algorithm value as "none" and get the flag.

<img width="1920" height="1020" alt="Screenshot (40)" src="https://github.com/user-attachments/assets/63315e58-db6e-48ba-ba1e-309a970122e7" />

# Flag
Flag: "nite{50_y0u_kn0w_h0w_jw75_w0rk_n0w?}"
# Resources
https://portswigger.net/web-security/jwt

https://www.jwt.io/
