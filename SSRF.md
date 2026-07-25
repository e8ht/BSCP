# SSRF

---

<img width="720" height="549" alt="image" src="https://github.com/user-attachments/assets/c091db44-b804-4ec7-84da-02bd3caaa860" />

<img width="722" height="770" alt="image" src="https://github.com/user-attachments/assets/c1ceb8b8-566e-4b26-bd3b-511a68fc1cb1" />

<img width="713" height="325" alt="image" src="https://github.com/user-attachments/assets/343a828a-d871-4392-aab8-96ae47dba10a" />







//Lab -- 

- enumerate the web
- check `/admin` -- not accessible directly
- click on check stock
- on repeater, swap in loopback address with `/admin` uri in `stockApi` param
- and we can access `/admin`

<img width="1247" height="426" alt="image" src="https://github.com/user-attachments/assets/51a98342-92d1-411e-86ce-3d238cb6d24d" />

- now delete carlos with `http://127.0.0.1/admin/delete?username=carlos`
- lab solved

<img width="1159" height="383" alt="image" src="https://github.com/user-attachments/assets/bfe984cd-5c39-4550-a496-df2915854afc" />


---

<img width="722" height="727" alt="image" src="https://github.com/user-attachments/assets/8e0c4f02-1e32-4fd5-884b-754caf1e6d80" />



//Lab -- Basic SSRF against another back-end system

- find check stock endpoint
- swap in `192.168.0.1/admin` under stockapi value -- and got 400 error

<img width="1031" height="387" alt="image" src="https://github.com/user-attachments/assets/341687af-2d64-4af6-a5a4-96340c6cdece" />

- on intruder, set numbers payload from 1-255 -- sniper mode
- then we got a 200 OK with `192.168.0.9`

<img width="1139" height="562" alt="image" src="https://github.com/user-attachments/assets/54ad9018-1cff-46dd-994c-aeed21f07d15" />

- now on repeater we go ahead and delete carlos with `http://192.168.0.9:8080/admin/delete?username=carlos`

<img width="973" height="385" alt="image" src="https://github.com/user-attachments/assets/a151c1a7-3399-4f3d-b774-8574b5c5d986" />


---

<img width="737" height="424" alt="image" src="https://github.com/user-attachments/assets/dd7a825b-deda-4773-aeb9-e0ef2701f89b" />


//Lab -- SSRF with blacklist-based input filter

- on stock check feature we try accessing the back end with `http://localhost/admin` -- but blocked

<img width="1073" height="379" alt="image" src="https://github.com/user-attachments/assets/8c66da8a-f9c5-46ff-962c-427ec34afe4a" />

- try `double url encoding` and `capitalizing` some chars and it works

<img width="1253" height="417" alt="image" src="https://github.com/user-attachments/assets/823811a9-b7a6-4cb0-856f-be6d82b0235e" />

- delete carlos with `stockApi=http://127.0.0.%25%33%31/aDmiN/delete?username=carlos` -- and lab solved

<img width="1172" height="392" alt="image" src="https://github.com/user-attachments/assets/dd08f77c-0bc0-4728-91d0-13c9941ce2e2" />


---


<img width="722" height="513" alt="image" src="https://github.com/user-attachments/assets/7bbd87f1-5cbc-4cbc-850e-feb98d4137b6" />

//Lab -- SSRF with whitelist-based input filter

- had to use `stock.weliketoshop.net` as suggested by the error -- it's been whitelisted to this url
- try using `@` to suggest credentials usage
- getting 500Error suggests we may have successfully accessed the endpoint
- place `localhost` in the beginning of the url
- then try `#` to suggest `url fragment` and it gets blocked
- so then try `double url encode` the `#` to `%25%32%33`
- and finally we can access `/admin`

<img width="1083" height="387" alt="image" src="https://github.com/user-attachments/assets/ff1d2bf2-7953-4e0b-9474-8619572a57a7" />

- delete carlos
- and lab solved

<img width="1246" height="389" alt="image" src="https://github.com/user-attachments/assets/77d6a00f-1033-4f6d-88a6-ac034ea121b0" />

---

<img width="714" height="612" alt="image" src="https://github.com/user-attachments/assets/d649ef38-0880-4c61-8987-e4be02f16c66" />

//Lab -- 

- found path param in the GET request of next product url
- try swapping in `localhost/admin` -- but it's not reachable
  
<img width="1023" height="370" alt="image" src="https://github.com/user-attachments/assets/8fb132fd-e99e-4885-99e6-b3bfa714c094" />

- so we grab the entire uri and use it as value for `stockApi` param in stock check feature

<img width="1251" height="409" alt="image" src="https://github.com/user-attachments/assets/7c4ae9b9-83be-4b40-aa93-72873e557393" />

- delete carlos and lab solved

<img width="1250" height="405" alt="image" src="https://github.com/user-attachments/assets/fb493932-ab0d-4d3c-ace3-ad252b872f41" />


---


<img width="700" height="191" alt="image" src="https://github.com/user-attachments/assets/38877324-24ba-4011-9f6a-b3aaffcfe585" />


<img width="711" height="635" alt="image" src="https://github.com/user-attachments/assets/d0b9af7a-005c-4d9d-88eb-a9c2b7d8c7bc" />


---

## BLIND SSRF

---

<img width="725" height="622" alt="image" src="https://github.com/user-attachments/assets/d42b56dd-0822-487e-9257-ce40c8fa8c76" />


<img width="720" height="234" alt="image" src="https://github.com/user-attachments/assets/fe559db6-e947-4c64-92bb-ee4a76574810" />



//Lab: Blind SSRF with out-of-band detection

INCOMPLETE -- need burp collab -- burp pro


---

<img width="721" height="190" alt="image" src="https://github.com/user-attachments/assets/1a17ee11-7d4b-4f16-ab09-e074ea406111" />


//Lab: Blind SSRF with Shellshock exploitation


---


<img width="717" height="119" alt="image" src="https://github.com/user-attachments/assets/a3bc6739-b913-4545-9538-abe55a1f1a33" />























