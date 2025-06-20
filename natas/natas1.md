### Step-by-step:

#### 1. **Authenticate**

The request you showed includes this header:

```
Authorization: Basic bmF0YXMxOjBuekNpZ0FxN3QyaUFMeXZVOXhjSGxZTjRNbGtJd2xx
```

That base64 value decodes to:

```
natas1:0nzCiGAq7t2iALyvU9xcHlYN4MlkIwql
```

So it contains the previous level credentials:

* **Username**: `natas1`
* **Password**: `0nzCiGAq7t2iALyvU9xcHlYN4MlkIwql`



#### 2. **Open the page**

Use browser or curl:

```bash
curl -u natas1:0nzCiGAq7t2iALyvU9xcHlYN4MlkIwql http://natas1.natas.labs.overthewire.org/
```

You’ll get an HTML page. The **password is not visible in the browser** directly, but you’ll see a comment if you:

#### 3. **View the source code of the page**


in terminal:

```bash
curl -u natas1:0nzCiGAq7t2iALyvU9xcHlYN4MlkIwql http://natas1.natas.labs.overthewire.org/
```

Look for a comment like:

```html
<!-- The password for natas2 is iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq -->
```



### Result


* **Natas2 username**: `natas2`
* **Password**: `iX6IOfmpN7AYOQGPwtn3fXpbaJVJcHfq` (example)



### Next Step

Login to:
[http://natas2.natas.labs.overthewire.org](http://natas2.natas.labs.overthewire.org)
With the Natas2 credentials.




![image](https://github.com/user-attachments/assets/2fd360cd-bb6e-4684-a156-fb92e9e22888)

![image](https://github.com/user-attachments/assets/f47618ab-bdef-4f14-a977-67df53fffa52)



<!--The password for natas2 is TguMNxKo1DSa1tujBLuZJnDUlCcUAPlI -->
