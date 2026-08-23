
<img width="656" height="439" alt="image" src="https://github.com/user-attachments/assets/0d0aaa77-f2f3-4115-b23a-bb9ee986bc81" />

---

<img width="653" height="666" alt="image" src="https://github.com/user-attachments/assets/7721ad7a-8b3c-4dc6-a62b-3f97706c90ee" />

<img width="646" height="725" alt="image" src="https://github.com/user-attachments/assets/fad7c229-c8e7-4c79-a8a8-2d8b27247013" />

<img width="561" height="771" alt="image" src="https://github.com/user-attachments/assets/4385e371-14b4-4e5f-9841-fb266a8c6ab1" />


---

<img width="652" height="648" alt="image" src="https://github.com/user-attachments/assets/cff5d3bd-8afa-4098-b68e-b65be3fdd8b0" />


---

<img width="661" height="272" alt="image" src="https://github.com/user-attachments/assets/de93d256-1fe8-40d3-8396-fcb8afe59c29" />

#### //LAB: Excessive trust in client-side controls

- log in with `wiener : peter`
- add product to cart

<img width="996" height="398" alt="image" src="https://github.com/user-attachments/assets/b3c9f727-990d-4b3c-9885-d251f8c43695" />

- in repeater POST /cart -- change the value in price param to 8

<img width="994" height="412" alt="image" src="https://github.com/user-attachments/assets/1a73a6f0-79ff-4a73-adf6-5a156b8698f8" />


- refresh `cart` page -- and the price of the product is only `8 cents` per
- place order -- and lab solved

<img width="1019" height="433" alt="image" src="https://github.com/user-attachments/assets/96d712fe-7bc6-4419-bfe0-bfb44254d094" />


---

#### //LAB: 2FA Broken Logic



- got in our account

<img width="988" height="505" alt="image" src="https://github.com/user-attachments/assets/a4eabd1b-d4d2-4464-b633-b8b8d582b763" />



- observe from earlier that the GET request for /login2 may be injectable
- in the `verify` param

<img width="1248" height="314" alt="image" src="https://github.com/user-attachments/assets/123c54dd-25a7-41df-bd7b-0508d0110118" />


- so go ahead and try using user carlos instead
- if successful an OTP should have been issued for carlos

<img width="1248" height="455" alt="image" src="https://github.com/user-attachments/assets/1ff8f476-0e0e-4a09-bca5-b1a620105750" />


- now here is the POST request for `/login2` from earlier for wiener user
- where we provide the OTP

<img width="1240" height="384" alt="image" src="https://github.com/user-attachments/assets/d1f38204-4a3f-4f1d-950f-2c7d99fdc9dc" />


- send it to intruder
- `sniper` attack
- `numbers` payload
- `0000` to `9999`
- min and max integer digits `4`

<img width="1558" height="479" alt="image" src="https://github.com/user-attachments/assets/1847b35d-00d5-44e4-a951-97ea69d4a276" />



- finally we got it -- `0387`
- key it in to access carlos account page and lab solved

<img width="1146" height="572" alt="image" src="https://github.com/user-attachments/assets/9ba9fe9d-7c61-4f4a-aac1-ef6e09b41ff5" />







---


<img width="650" height="622" alt="image" src="https://github.com/user-attachments/assets/846c1d3e-f111-4a53-8b3f-f0f84b9353b5" />


<img width="657" height="451" alt="image" src="https://github.com/user-attachments/assets/bfdfddb1-ed94-4608-8351-f3140f7708a1" />


#### //LAB:


- try and inject into quantity param
- and apparently we can successfully add a negative quantity

<img width="974" height="398" alt="image" src="https://github.com/user-attachments/assets/c6045f25-62ae-44dd-bff3-670a1e7b5c75" />

- however to successfully place an order -- the total price has to be positive -- above 0

<img width="950" height="602" alt="image" src="https://github.com/user-attachments/assets/62676259-45c9-4fbc-b95a-3c2cdd90313a" />




- go ahead and add one 1337 leet jacket to our cart
- the total price is now $1337

<img width="992" height="413" alt="image" src="https://github.com/user-attachments/assets/f15d2118-67ad-4dcd-a372-4ecc8a958e1d" />




- now change the productId to another
- and make sure it's a negative value
- to subtract out the the leet jacket $1337 price -- to under $100 which is our store credit

<img width="960" height="398" alt="image" src="https://github.com/user-attachments/assets/341f75a5-586d-4412-8122-ebe313bd0604" />





<img width="934" height="647" alt="image" src="https://github.com/user-attachments/assets/09394cb9-1bcc-41ea-9c72-b752bcab5177" />

- and lab solved

<img width="947" height="417" alt="image" src="https://github.com/user-attachments/assets/d18b66cf-4e1b-4fc8-b37e-32220d6e04a9" />


**LESSON LEARNED -- gotta be smart about it


---

#### //LAB: Low-level Logic Flaw


- in repeater POST request /cart -- found that we may be able to manipulate `quantity` param
- play around on repeater for awhile and found that we cannot add more than 2 digits at a time
- so 99 is the max value

<img width="1136" height="426" alt="image" src="https://github.com/user-attachments/assets/cf0ffaf5-73a1-4fe2-9498-95accbd63ea6" />


- via intruder -- found out that we could get the amount to loop back after max integer value of `2147,483,647`

<img width="930" height="591" alt="image" src="https://github.com/user-attachments/assets/3f784bd6-ae4a-45e4-aff9-f1b845880466" />


- so now after some calculations -- we need to send 323 payloads of 99
- set payload to Null
- generate 323 payloads
- in resource pool -- set maximum concurrent requests to 1
- then start attack

<img width="1562" height="460" alt="image" src="https://github.com/user-attachments/assets/ad7666fe-5b7b-4b75-898e-6055ec9d88aa" />


- wait awhile for it to complete

<img width="1082" height="332" alt="image" src="https://github.com/user-attachments/assets/94374a92-9b15-4ecc-a0a6-0df505b3d2da" />


- now then add 47 to quantity param to get the amount down to -1221.96

<img width="1020" height="408" alt="image" src="https://github.com/user-attachments/assets/53219eec-cb79-43d0-9b21-1e68c70c4966" />


- now add other products to get the total amount between $1 to $100

<img width="891" height="624" alt="image" src="https://github.com/user-attachments/assets/52019fd6-2dab-4624-ab49-83c4203ac10f" />


- place order
- and finally lab solved

<img width="943" height="442" alt="image" src="https://github.com/user-attachments/assets/e07e95a3-6188-4c38-be53-c790f64f267b" />


---
#### //LAB: Inconsistent handling of exceptional input


- first create a normal account -- then we got an email for account activation
- click the link to activate the account and we got a normal account
- next try and add a bunch of chars as username and create another account
- got the email to activate -- then again click the link to complete registration

<img width="1020" height="616" alt="image" src="https://github.com/user-attachments/assets/10270eae-c4d9-429b-b4d6-66c189fe6bf6" />


- log in to our account with the creds we just registered earlier
- notice that the email is truncated to 255 chars

<img width="1062" height="434" alt="image" src="https://github.com/user-attachments/assets/0a91f225-6b93-4590-b8e0-368b80587cca" />

- now we need to craft an email payload to fit exactly 255 chars
- gotta include `@dontwannacry.com` -- which is 17 chars
- so we need 238 chars username
- whip it up with python -- `python3 -c 'print("a"*238)'`

<img width="1233" height="75" alt="image" src="https://github.com/user-attachments/assets/11261bc5-558a-4f2e-93c1-084079c878c6" />

- now we got
```
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa@dontwannacry.com.exploit-0ac9009a03335dac8127ba83016c00ba.exploit-server.net
```

- it should get truncated to 255 chars to just -- `aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa@dontwannacry.com`
- note that we need the `.` after `.com` to signify that `@dontwannacry.com` is a subdomain
- and we got an email confirmation to activate our new account


<img width="990" height="623" alt="image" src="https://github.com/user-attachments/assets/caeb8cb2-e2e9-4e8d-a4ec-53eb52942136" />


- got in as `test3` user
- notice there's an admin panel

<img width="946" height="407" alt="image" src="https://github.com/user-attachments/assets/58b690fa-3356-4722-9066-b381204656b8" />



- we're in admin panel
- here we can delete user carlos
- and lab solved

<img width="945" height="358" alt="image" src="https://github.com/user-attachments/assets/ec83fb6b-f922-472c-b06a-34cc6be0823f" />

<img width="953" height="415" alt="image" src="https://github.com/user-attachments/assets/05a87477-923c-4680-9f52-7b89cd1eb4c9" />



---


<img width="655" height="341" alt="image" src="https://github.com/user-attachments/assets/8353ee0a-758a-40aa-8427-b8ae99b80695" />


#### //LAB: Inconsistent security controls



- try and register a new account
- notice that users with email registered to `@dontwannacry.com` domain -- should have priv access


<img width="1046" height="478" alt="image" src="https://github.com/user-attachments/assets/15bd0940-63be-4d72-ac82-3d5b5f4af0e2" />



- try and change our email to test@dontwannacry.com
- and its a success

<img width="997" height="487" alt="image" src="https://github.com/user-attachments/assets/5dbeb979-22d6-4fea-90a7-9c98cce86b26" />


- in admin panel we can delete user carlos

<img width="1040" height="394" alt="image" src="https://github.com/user-attachments/assets/f91c1e60-35b3-4c56-8dca-c57c5be15004" />


- go ahead and delete carlos
- and lab solved

<img width="994" height="452" alt="image" src="https://github.com/user-attachments/assets/0558b25a-e77b-49ec-9616-b8132335e3cb" />



---

<img width="663" height="423" alt="image" src="https://github.com/user-attachments/assets/42539d0e-ad2d-4271-882c-19c6685b281f" />


#### //LAB: Weak isolation on dual-use endpoint



- attempt to change username to `administrator`
- but it says current password is incorrect


<img width="1250" height="414" alt="image" src="https://github.com/user-attachments/assets/8112455c-2a22-4e38-b4d3-cbd06369ed6b" />



- try and remove the `current-password` param altogether
- and it appears to be successful -- the password for administrator user should already be changed to `peter`

<img width="1261" height="481" alt="image" src="https://github.com/user-attachments/assets/bd290424-a638-4306-ac90-16a7118acd33" />




- try and log in with `administrator : peter`
- and we got in


<img width="938" height="644" alt="image" src="https://github.com/user-attachments/assets/6765bee1-45bd-41a0-8a15-00228c8939d8" />


- in admin panel we could delete carlos


<img width="945" height="330" alt="image" src="https://github.com/user-attachments/assets/1ae15eba-b6e7-45e7-b849-5d3016f853ac" />


- and lab solved

<img width="938" height="392" alt="image" src="https://github.com/user-attachments/assets/d148c79d-1a25-4ab9-b4eb-2c6452bb8a14" />


---


<img width="667" height="229" alt="image" src="https://github.com/user-attachments/assets/cb2ab7ac-86fa-4a63-a175-562ec41d69d9" />




#### //LAB: 2FA Simple Bypass



- first log in with `wiener : peter`
- grab the 2fa code from the email client
- then we got in our account

<img width="933" height="433" alt="image" src="https://github.com/user-attachments/assets/d08d8c12-e135-4307-addf-d24947bb0de4" />


- now log out and log back in with `carlos : montoya`

- prompted with 2fa code -- try and simply change the uri in the browser to `/my-account` in an attempt to bypass

<img width="935" height="322" alt="image" src="https://github.com/user-attachments/assets/08f2c30f-4686-4e63-bbf1-0e33a92d8d47" />


- and lab solved just like that

<img width="904" height="426" alt="image" src="https://github.com/user-attachments/assets/5ecb9562-2e10-4663-ba37-27bbfb28b8a2" />



---



<img width="655" height="352" alt="image" src="https://github.com/user-attachments/assets/a9340328-b7f0-45f2-a64d-5947a273e87e" />


#### //LAB: Insufficient workflow validation



- first play around with the site
- add `itemID 2` to the cart and place order

<img width="1072" height="397" alt="image" src="https://github.com/user-attachments/assets/3e1ed0cc-16ed-4c06-ad9b-79cd795fee76" />


- order went through
- notice that once order is placed -- we get an order confirmation page GET request `/cart/order-confirmation?order-confirmed=true`


<img width="1245" height="312" alt="image" src="https://github.com/user-attachments/assets/d314f539-6f11-45c4-accc-ff555e743d0b" />



- add l33t jacket to the cart
- note the session cookie

<img width="984" height="649" alt="image" src="https://github.com/user-attachments/assets/bfaa8f28-22ea-4c11-8a11-8eb19a65c53c" />

<img width="936" height="493" alt="image" src="https://github.com/user-attachments/assets/3eb148fb-c223-4d7e-b0cb-301946ed3952" />



- now that we have the l33t jacket in the cart
- the session cookie in the browser matches one in burp from earlier
- try and send the order-confirmation request `GET /cart/order-confirmation?order-confirmed=true`

<img width="1250" height="308" alt="image" src="https://github.com/user-attachments/assets/84783ca0-c8e8-4062-a9cc-65b1d53ebc17" />



- apparently the order went through
- and lab solved

<img width="998" height="420" alt="image" src="https://github.com/user-attachments/assets/bf22d453-790f-4f5e-9e3c-739a7a94b6ab" />




---

#### //LAB: Auth bypass via flawed state machine




- try and log in with `wiener : peter` normally
- notice we're redirected to `/role-selector` endpoint after providing creds to log in at `POST /login`

<img width="1244" height="369" alt="image" src="https://github.com/user-attachments/assets/a19d4698-f828-432e-a6ba-8170b029e38a" />


- try and navigate to `/admin`
- not accessible -- but exists
- log out
- turn intercept on in burp
- log back in with `wiener : peter`
- forward the `POST /login`
- now then drop the `GET /role-selector` on burp

- <img width="1012" height="289" alt="image" src="https://github.com/user-attachments/assets/ca2b5646-26cd-4c4c-9353-65bdadefdab8" />



- now then if we navigate to `/admin` -- we're admin!
- we've bypassed auth to get admin access
- likely due to `default admin role assignment` not being overwritten by `/role-selector`

<img width="1320" height="409" alt="image" src="https://github.com/user-attachments/assets/70013555-161f-443a-9ded-0d7c8fc46caa" />



- delete carlos and lab solved

<img width="1297" height="491" alt="image" src="https://github.com/user-attachments/assets/3cdb5b1b-8ab4-4d06-8f92-061ceb2776a6" />



---


<img width="655" height="696" alt="image" src="https://github.com/user-attachments/assets/0b69d17d-bc27-4d37-a912-4c9092653b3e" />



#### //LAB: Domain-Specific Flaws


- so apparently there are 2 coupons
- one at the top of the page -- `NEWCUST5`
- the other is at the bottom after we sign up for a newsletter -- `SIGNUP30`
- apply both coupons

<img width="1219" height="896" alt="image" src="https://github.com/user-attachments/assets/39fb9862-5664-491a-9b68-3c83420f2e83" />



- try and apply the same coupon twice in a row would fail

<img width="1139" height="383" alt="image" src="https://github.com/user-attachments/assets/133f9a02-2e76-4b71-9e68-dfdf984fe86c" />



- applying the two coupons alternatively works

<img width="1251" height="374" alt="image" src="https://github.com/user-attachments/assets/e1f3dad5-1fe3-4468-a7e2-315f15f6390d" />

<img width="1251" height="383" alt="image" src="https://github.com/user-attachments/assets/61a4e2c1-c9e3-4fab-9fca-696dfeae7838" />

<img width="1088" height="907" alt="image" src="https://github.com/user-attachments/assets/1b620614-5c55-4442-b480-5adc0035e77f" />




- and lab solved

<img width="1095" height="690" alt="image" src="https://github.com/user-attachments/assets/ad444665-0758-46e5-a541-c1b6dcfb4d5c" />

LESSONS LEARNED: -- gotta be creative about it


---

#### //LAB:



- sign up for a nesletter and get a coupon code -- `SIGNUP30`
- there's a $10 gift card available for purchase


<img width="1142" height="731" alt="image" src="https://github.com/user-attachments/assets/84e1bc9b-a44e-421d-b35d-d2581fa4bf6c" />




MACRO








- send `my-account` to intruder
- sniper attack
- 412 null payloads (* $3) to get $1236 + existing $103 == $1339 total -- just enough to purchase the l33t jacket
- in resource pool -- set maximum concurrent request to be `1`

<img width="1552" height="386" alt="image" src="https://github.com/user-attachments/assets/9ba7785d-3dc4-46f8-9ac0-13fdb80eb8c4" />






- finally we got enough credits

<img width="1143" height="522" alt="image" src="https://github.com/user-attachments/assets/7b5469d2-a207-4f48-9533-2a9e63da8eb8" />

<img width="1060" height="648" alt="image" src="https://github.com/user-attachments/assets/2c969fbe-7c30-4acf-a902-11ed435d38c9" />


- finally lab solved

<img width="1090" height="411" alt="image" src="https://github.com/user-attachments/assets/49c834f5-4744-411f-95be-01da221bf13a" />















