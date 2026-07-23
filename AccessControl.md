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



















































