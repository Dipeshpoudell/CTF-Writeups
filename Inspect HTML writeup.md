# Inspect HTML writeup

### Description:

Can you get the flag

### Initial recon:

The website appeared to be a simple static HTML page. Based on the challenge description, I decided to inspect the source code for any hidden information.

![image.png](Inspect%20HTML%20writeup/image.png)

### Exploitation:

I hit inspect to the vulnerable site and the flag was right there in plain text and the flag was revealed.

![image.png](Inspect%20HTML%20writeup/image%201.png)

### **Result:**

- The flag was exposed directly in the page source.
- No authentication or input manipulation was required.
- The challenge was solved by simple **client-side inspection**.
- The hidden flag was successfully retrieved.

### **Key Learning:**

- Never store sensitive data like flags in client-side HTML.
- Always inspect the source code during initial recon.
- Client-side security alone offers **zero real protection**.