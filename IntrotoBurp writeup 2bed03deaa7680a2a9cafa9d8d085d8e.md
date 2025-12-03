# IntrotoBurp writeup

**Category:** Web Exploitation

### **Description:**

This challenge focuses on understanding how web applications handle OTP verification and how Burp Suite can be used to manipulate requests. The goal is to bypass the OTP check and retrieve the hidden flag.

### **Initial Recon:**

After opening the provided URL, a registration page appears. I filled in the required details and clicked the **Register** button. This redirected me to a new page asking for an OTP.

![image.png](IntrotoBurp%20writeup/image.png)

I entered a random OTP and submitted it. As expected, the application responded with **“Invalid OTP.”**

![image.png](IntrotoBurp%20writeup/image%201.png)

To analyze this behavior, I returned to the OTP page and captured the request using **Burp Suite**, since the challenge specifically requires its use.

### **Exploitation:**

The OTP verification request was sent using the **POST** method. I forwarded this request to **Burp Repeater** and tested multiple inputs including:

- Random numbers
- Special characters
- SQL injection payloads
- Blank input

In all cases, the server still returned **“Invalid OTP.”**

![image.png](IntrotoBurp%20writeup/image%202.png)

Since the OTP was being sent in the request body, I removed the entire parameter from the POST body and resent the request.

This time, instead of an error, the application directly revealed the **flag**.

![2025-12-03_20-52.png](IntrotoBurp%20writeup/2025-12-03_20-52.png)

### **Result:**

- OTP validation was bypassed by removing the OTP parameter from the POST request.
- The application returned the **flag** without proper verification.

### **Key Learning:**

- Always analyze request structure using interception tools like Burp.
- Missing input validation can completely break authentication systems.
- Server-side checks must never trust client-side input blindly.