# Crack the gate 1 Writeup

***Category***: Web exploitation

## Description:

We’re in the middle of an investigation. One of our persons of interest, ctf player, is believed to be hiding sensitive data inside a restricted web portal. We’ve uncovered the email address he uses to log in: `ctf-player@picoctf.org`. Unfortunately, we don’t know the password, and the usual guessing techniques haven’t worked. But something feels off... it’s almost like the developer left a secret way in. Can you figure it out?

## Initial Recon:

A web portal is given on the start of the instance with an login username.

![image.png](Crack%20the%20gate%201%20Writeup/image.png)

 My first thought was to try bruteforce it or guess the password but the description further said that the guessing technique have not worked so i started by checking the form with SQL injection by using the payload  `" OR 1 = 1 -- -` but it gave an error saying “Invalid credentials”.

![image.png](Crack%20the%20gate%201%20Writeup/image%201.png)

So i checked the page source where i saw an unusual comment 

![image.png](Crack%20the%20gate%201%20Writeup/image%202.png)

I copied the text and decoded it using an online decoder and the text was

<!-- NOTE: Jack - temporary bypass: use header "X-Dev-Access: yes" -->

Looking at this piece of comment i loaded up my Burp Suite and turned my intercept on to get the packet and put `X-Dev-Access: yes`  header into the packet and forwarded it and it gave me the flag. 

![image.png](Crack%20the%20gate%201%20Writeup/image%203.png)

## Result:

- The portal granted access without a password.
- The flag was displayed on the page.

## Key learning:

- HTML comments can leak **critical security information**.
- Developers sometimes leave **debug backdoors** in headers.
- Authentication must always be validated **server-side**.