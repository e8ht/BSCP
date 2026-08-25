
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

#### //LAB: Infinite money logic flaw


- check the features of the site
- at the bottom -- sign up for a newsletter and get a coupon code -- `SIGNUP30`
- there's a $10 gift card available for purchase -- add it to cart
- place the order and we'd have $93 store credit left
- then redeem the gift card -- and we'd have $103
- so the plan is to see if we can rinse and repeat this money glitch

<img width="1142" height="731" alt="image" src="https://github.com/user-attachments/assets/84e1bc9b-a44e-421d-b35d-d2581fa4bf6c" />

- it's likely best to use Burp Macro to tackle this
- Settings --> sessions --> add new session handling rules `gift card abuse`

<img width="1168" height="347" alt="image" src="https://github.com/user-attachments/assets/7b6b0d6c-dd59-4f22-9703-bfd010dada41" />

- under scope, include all urls

<img width="960" height="414" alt="image" src="https://github.com/user-attachments/assets/be723248-96a8-4f03-9580-88f9dd88813f" />

- back to details --> add `run a macro` --> add again to open macro recorder
- select the following 5 requests:
    1. `POST /cart`
    2. `POST /cart/coupon`
    3. `POST /cart/checkout`
    4. `GET /cart/order-confirmation`
    5. `POST /gift-card`
- select `/cart/order-confirmation` --> configure item

<img width="1071" height="600" alt="image" src="https://github.com/user-attachments/assets/9bdbc9a6-e159-454f-b67d-7aa0dce7eea6" />



- add custom param --> name it `gift-card` --> highlight the giftcard code

<img width="679" height="647" alt="image" src="https://github.com/user-attachments/assets/4fca7eea-25fc-4774-a59c-67a448f8d8bc" />


<img width="1064" height="839" alt="image" src="https://github.com/user-attachments/assets/7b05154e-4e1a-4c68-8311-f09953aba468" />
 

- now select `/gift-card`

<img width="1072" height="598" alt="image" src="https://github.com/user-attachments/assets/e36bc474-7843-42d1-9d2f-cd34eb142f75" />

- configure item --> under parameter handling `gift-card`, select derived from prior response -- response4

<img width="676" height="649" alt="image" src="https://github.com/user-attachments/assets/881d7e52-d7be-475e-a77f-fc48ee74cbd6" />

- click `test macro`
- check and all is good -- we have a loop of: 1) order is placed  -- 2) gift card code is collected -- 3) gift card is redeemed
- now send `/my-account` request to intruder
- sniper attack
- 412 null payloads (* $3) to get $1236 + existing $103 == $1339 total -- just enough to purchase the l33t jacket
- in resource pool -- set maximum concurrent request to `1`

<img width="1552" height="386" alt="image" src="https://github.com/user-attachments/assets/9ba7785d-3dc4-46f8-9ac0-13fdb80eb8c4" />




- wait a good while and finally we got enough credits

<img width="1143" height="522" alt="image" src="https://github.com/user-attachments/assets/7b5469d2-a207-4f48-9533-2a9e63da8eb8" />

<img width="1060" height="648" alt="image" src="https://github.com/user-attachments/assets/2c969fbe-7c30-4acf-a902-11ed435d38c9" />



- go ahead and complete the order for l33t jacket
- and finally lab solved

<img width="1090" height="411" alt="image" src="https://github.com/user-attachments/assets/49c834f5-4744-411f-95be-01da221bf13a" />



---


<img width="657" height="344" alt="image" src="https://github.com/user-attachments/assets/2589a861-ad19-42b3-9509-c12cf1505db7" />


#### //LAB: Auth bypass via encryption oracle




- log in with `wiener : peter`
- try and post a comment
- notice there's an error displayed on the page -- ` Invalid email address: test3.org ` -- if email format is wrong

<img width="1222" height="346" alt="image" src="https://github.com/user-attachments/assets/5d2947f1-0aa7-436f-85c7-e5b54302017c" />


- on burp this is the request to post the comment
- notice the set-cookie cookie

<img width="1250" height="416" alt="image" src="https://github.com/user-attachments/assets/12cfe258-c788-4789-b570-dc048dec2e27" />


- and here is the subsequent GET request `/post`
- observe that the notification cookie is likely the `Invalid email address: test` error message we get in the response

<img width="1249" height="331" alt="image" src="https://github.com/user-attachments/assets/a5b5ab2d-3d71-4834-a656-c5ae883ae126" />


- this means that we can use the POST `/post/comment` request email param to encrypt cookies
- and we can use the subsequent GET `/post` request to decrypt cookies
- so here we try and use the GET request to decrypt our cookie -- and we got it

<img width="1248" height="322" alt="image" src="https://github.com/user-attachments/assets/62273ad2-5fa3-416c-b185-b8be766ea9b3" />



- and then naturally we try to forge administrator's cookie
- by encrypting it with the POST `/post/comment`

<img width="1249" height="411" alt="image" src="https://github.com/user-attachments/assets/b9b99b1e-dbb1-43d8-a8c3-cae51c0076e6" />




- google and found that it's a blocked-based encryption algo
- input length has to be in multiple of 16 -- so we need to pad `Invalid email address` with enough bytes
- so add 9 chars just before our cookie payload `888888888administrator:1787589492591`
- decrypt it and it seems to work

<img width="1250" height="338" alt="image" src="https://github.com/user-attachments/assets/13fcee0b-a662-4621-b1de-f3e1cc58ab1d" />



- now we have to somehow get rid of the `invalid email address`
- we url-decode, base64 decode, then remove the first 32 bytes of the cookie

<img width="1552" height="435" alt="image" src="https://github.com/user-attachments/assets/47b79e54-981d-4409-b794-888963fcf7b8" />

<img width="1558" height="360" alt="image" src="https://github.com/user-attachments/assets/d433b797-dd7c-4e8e-bce4-f49afbc6006f" />




- once we apply changes -- we get a newly forged cookie

<img width="1558" height="357" alt="image" src="https://github.com/user-attachments/assets/9a0659b6-b18f-4b39-ac7c-5e5edb5490c6" />




- now try and decrypt our new forged cookie this time and looks like we got it

<img width="1245" height="321" alt="image" src="https://github.com/user-attachments/assets/defaa49e-9be6-454c-a53e-00b273c028c4" />





- swap in our forged cookie and remove session cookie param at `/`

<img width="1250" height="327" alt="image" src="https://github.com/user-attachments/assets/5d2d8755-cc46-48ff-92c0-a116c187441f" />




- access `/admin`

<img width="1252" height="571" alt="image" src="https://github.com/user-attachments/assets/cf67ac9b-b204-4ba8-98b3-eeed573692de" />



- go ahead and delete carlos user

<img width="1247" height="319" alt="image" src="https://github.com/user-attachments/assets/95c1458c-09ca-4b5e-975b-7ada5147b7d6" />



- and lab solved

<img width="1243" height="337" alt="image" src="https://github.com/user-attachments/assets/6889fe86-14b4-40cf-aa30-281b801160fe" />

<img width="1188" height="344" alt="image" src="https://github.com/user-attachments/assets/cd45a9fc-d5bb-4939-814a-1fd55e9525f2" />




---


<img width="655" height="451" alt="image" src="https://github.com/user-attachments/assets/e98d7e8d-35aa-4e2f-bb7c-a98cef847c7e" />



#### //LAB:






- read this `https://portswigger.net/research/splitting-the-email-atom`
- then proceed to register for an account
- try this iso payload as seen in the research article -- but it is blocked
- `=?iso-8859-1?q?=61=62=63?=tool@ginandjuice.shop`

<img width="1247" height="385" alt="image" src="https://github.com/user-attachments/assets/d382c7ee-7c07-4c12-85b9-8849502e92aa" />


- utf-8 payload also fails -- blocked
- `=?utf-8?q?=61=62=63?=tool@ginandjuice.shop`

<img width="1246" height="384" alt="image" src="https://github.com/user-attachments/assets/43c45247-6aad-4935-b4e3-0c4688bfdfa9" />



- now try utf-7
- try and url-encode it as well or it breaks
- and it seems to have gone through
- but there's no activation email in our mailbox

<img width="1239" height="518" alt="image" src="https://github.com/user-attachments/assets/1cf2d952-c19a-44c0-9758-f3769e6e9f9f" />


- try cyberchef UTF-7 encoding
- but it fails

<img width="1228" height="614" alt="image" src="https://github.com/user-attachments/assets/fe671810-5f55-4142-8cdf-26fd13f1558f" />



- eventually this works `=?utf-7?q?attacker%26AEA-exploit-0a0200a103532e2b81db8d59013b0098.exploit-server.net%26ACA-?=@ginandjuice.shop`
- the `&AEA` is `@`
- the `&ACA` is ` ` space
- note that we need to url-encode the `&`



<img width="1240" height="524" alt="image" src="https://github.com/user-attachments/assets/e0592340-fbf8-4c2b-8288-eabc27807229" />




- finally got an activation email

<img width="1156" height="541" alt="image" src="https://github.com/user-attachments/assets/48fe70b8-2817-4564-af61-10a324ea439d" />


- click on the link
- and log in with our creds

<img width="1193" height="566" alt="image" src="https://github.com/user-attachments/assets/e69fd7cc-cb98-45fd-866e-e297bf851e81" />


- hit admin panel
- delete carlos
- and lab solved finally

<img width="1185" height="473" alt="image" src="https://github.com/user-attachments/assets/2df1bed0-59ed-4778-85e0-868189c3de78" />










