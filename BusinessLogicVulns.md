
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












