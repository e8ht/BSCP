# ACCESS CONTROL -- https://portswigger.net/web-security/access-control#vertical-access-controls

---

<img width="924" height="432" alt="image" src="https://github.com/user-attachments/assets/a890bb33-6f26-44ed-b10e-ad09ec2710bc" />


//Lab -- Unprotected admin functionality

- Check robots.txt
- simply access the disallowed uri
- delete carlos

---

<img width="919" height="262" alt="image" src="https://github.com/user-attachments/assets/65b3c031-505a-4703-9c7e-a53ca1a032ce" />


//Lab -- Unprotected admin functionality with unpredictable URL

- view page source
- copy paste admin uri
- delete carlos

<img width="859" height="232" alt="image" src="https://github.com/user-attachments/assets/94c9fff4-c771-4b69-b2dd-77bf2fd0edbb" />

---

<img width="919" height="413" alt="image" src="https://github.com/user-attachments/assets/3c2f3936-6a79-471c-be05-be08aafef420" />


//Lab -- User role controlled by request parameter

- visit /admin
- inspect
- change admin value to true
- delete carlos

<img width="687" height="97" alt="image" src="https://github.com/user-attachments/assets/8f5c6d09-50e5-4eaa-872e-e8ef31342726" />

---

//Lab -- User role can be modified in user profile

- log in as wiener:peter
- fire up burp to intercept or just switch on foxyproxy
- change the email
- on burp, send change-email api to repeater
- notice that when we send the request -- there's a roleid param also sent
- add "roleid":2 to our JSON in request body -- **this is new**
- send it -- then we should see admin panel accessible in the response
- at this point our cookie as wiener should already be tied to roleid=2 which is admin's
- on firefox -- visit /admin
- delete carlos

<img width="1060" height="432" alt="image" src="https://github.com/user-attachments/assets/96020274-4412-4e03-b4a9-446ea9da455c" />

---


<img width="935" height="427" alt="image" src="https://github.com/user-attachments/assets/478a753a-a43f-4449-8fdc-815299f5dd40" />


//Lab -- URL-based access control can be circumvented

- first we try and add X-Original-URL: /admin
- note don't change the real query string next to GET
- then we can see we can access /admin and the apis to delete users

<img width="1252" height="422" alt="image" src="https://github.com/user-attachments/assets/eaefbabb-4b8f-4717-bb8d-45db04f419b3" />

- try and delete user but apparently we can't just dump the entire api in X-Original-URL header like that

<img width="1250" height="316" alt="image" src="https://github.com/user-attachments/assets/e24e2fee-451c-48b9-9234-2127347f10b7" />

- this works -- put username in the real query string next to GET

<img width="1254" height="309" alt="image" src="https://github.com/user-attachments/assets/a7c45724-f9c0-4b00-b4bb-867ebc1528a4" />


---

<img width="952" height="121" alt="image" src="https://github.com/user-attachments/assets/674734d3-5e35-4c32-89d1-e42eb0010898" />

//LAB -- Method-based access control can be circumvented

- log in as administrator and play with admin panel at /admin-roles

<img width="938" height="371" alt="image" src="https://github.com/user-attachments/assets/1c937349-c1b5-4c10-908e-609aec67f8f6" />

- log out then log back in as wiener:peter -- then copy our session cookie

<img width="1094" height="299" alt="image" src="https://github.com/user-attachments/assets/f340e8a8-16ef-4374-b70a-fe868800d169" />

- paste our session cookie into /admin-roles
- also change username param to wiener -- and action to upgrade
- then try and send the request and we'd get "missing param username"

<img width="1050" height="375" alt="image" src="https://github.com/user-attachments/assets/478a2cac-8ef6-4c21-99b2-02c7dc619a3c" />


- then right click and change request method -- we'd get a GET request instead with no request body
- and notice we get a redirection -- 

<img width="928" height="331" alt="image" src="https://github.com/user-attachments/assets/216da613-1510-426d-8054-eefc431322a8" />

- follow the redirection and it's lab solved

<img width="1245" height="324" alt="image" src="https://github.com/user-attachments/assets/bf6f903f-0aee-4d0c-8469-5b5194889032" />


---

<img width="953" height="790" alt="image" src="https://github.com/user-attachments/assets/cd6ba896-9b8e-42cb-af09-72ab3e2b9a27" />


//Lab -- 

- log in with wiener:peter
- change the value in id param to carlos
- and lab solved just like that

<img width="696" height="495" alt="image" src="https://github.com/user-attachments/assets/70fe68b8-9f4d-475c-a4bd-9b6c3852b506" />




---

<img width="945" height="129" alt="image" src="https://github.com/user-attachments/assets/3bb32b4b-bc08-4d85-9dac-0bcebfb7e65f" />


//Lab -- User ID controlled by request parameter, with unpredictable user IDs 

- browse through lab and comments
- found carlos guid in the url

  
<img width="949" height="370" alt="image" src="https://github.com/user-attachments/assets/7f7106e8-cfbc-460e-883e-22371637471e" />


- log in with wiener:peter
- swap in carlos's GUID in the url
- submit his API key

<img width="1181" height="479" alt="image" src="https://github.com/user-attachments/assets/2799824c-7268-4691-b8f6-01ffb331b657" />


---

<img width="956" height="123" alt="image" src="https://github.com/user-attachments/assets/38348c30-1605-4316-958b-2a8f82c44fc0" />

//Lab -- User ID controlled by request parameter with data leakage in redirect 

- log in with wiener:peter
- swap in 'carlos' in the id param in the url
- in burp, look at the 302 redirect response -- and we found carlos' API key leaking

<img width="1238" height="273" alt="image" src="https://github.com/user-attachments/assets/2ac906d3-8fe5-43d0-b635-4a1b6beaf92f" />


---


<img width="954" height="361" alt="image" src="https://github.com/user-attachments/assets/f16bd1d8-aa6d-4293-a884-90c3c82e8cda" />


//Lab -- User ID controlled by request parameter with password disclosure

- log in with wiener:peter
- swap in `administrator` in id param in the url -- we then see a masked password
- right click and inspect -- and find `i2vvzs9sf8q7rrlxtai8`
- log in with `administrator : i2vvzs9sf8q7rrlxtai8`
- delete carlos in admin panel

<img width="940" height="588" alt="image" src="https://github.com/user-attachments/assets/55893025-4ae0-45d5-81fd-2bb574f38a41" />


---


<img width="963" height="167" alt="image" src="https://github.com/user-attachments/assets/54e48bbd-fa48-4430-8aa5-0f4e770ed8ab" />

//Lab -- IDOR

- go to live chat and chat
- download transcript and notice we get 2.txt
- on burp repeater -- change 2.txt to 1.txt and send
- and found passwd `48wgghkqdq6pyixhgwnx`
- log in as carlos and lab solved


<img width="1247" height="351" alt="image" src="https://github.com/user-attachments/assets/a1f6e6d6-0a40-4195-b449-78db37218f52" />


---


<img width="953" height="433" alt="image" src="https://github.com/user-attachments/assets/0badbe24-95eb-4c71-9f72-8834e3a88949" />

//Lab -- Multi-step process with no access control on one step

- first log in as administrator and observe the admin panel requests
- try and upgrade carlos to admin at /admin-roles
- note that there are the initial and the subsequent confirmation requests

<img width="1249" height="361" alt="image" src="https://github.com/user-attachments/assets/0d1accb2-00b5-4ce8-a530-52c89a1ff5f9" />
<img width="1071" height="376" alt="image" src="https://github.com/user-attachments/assets/933c0613-2a40-4339-bdb4-207100fe274a" />

- log out then log back in as wiener -- copy our session cookie
- swap in our session cookie at the subsequent confirmation request /admin-roles from earlier
- and also change the username param to wiener

<img width="989" height="388" alt="image" src="https://github.com/user-attachments/assets/96eea3a8-4759-4c89-a927-5f97d2317c6f" />


- follow redirection and lab solved
<img width="1248" height="345" alt="image" src="https://github.com/user-attachments/assets/78ff284e-895c-4efa-a4f6-e6adf6353c39" />



---

<img width="958" height="263" alt="image" src="https://github.com/user-attachments/assets/7df9375a-a5b7-44ce-a3d3-e64211cf2990" />


//Lab -- Referer based access control

- log in as administrator and observe the admin panel at /admin-roles
- try and upgrade carlos -- note that it's a GET request
- also note that the referer header is from /admin

<img width="917" height="289" alt="image" src="https://github.com/user-attachments/assets/8c30b098-6cc5-4e2d-8ea6-60002beb3b0d" />


- log out and log back in as wiener
- grab our session cookie

<img width="1241" height="294" alt="image" src="https://github.com/user-attachments/assets/0f0c9887-8d05-4f61-8731-b1546e2fd160" />

- on /admin-roles from earlier where the referer header is /admin used for upgrading carlos -- we swap in our session cookie
- and change the username param to wiener

<img width="945" height="297" alt="image" src="https://github.com/user-attachments/assets/bb1e2c12-319b-405d-a862-ff9c849b1d2a" />


- send it and lab solved

<img width="1248" height="341" alt="image" src="https://github.com/user-attachments/assets/5c49e1db-eb2b-4acb-ac8e-fcac1213cf4e" />


---


<img width="937" height="431" alt="image" src="https://github.com/user-attachments/assets/d0843417-0430-45ff-a576-bbda5d338c55" />










































