## Goal

Find the password for **natas3** by testing **Natas2**.


## Step 1: Decode the Authorization Header

You shared:

```
Authorization: Basic bmF0YXMyOlRndU1OeEtvMURTYTF0dWpCTHVaSm5EVWxDY1VBUGxJ
```

### Decode it:

Use terminal or online base64 decoder:

```bash
echo bmF0YXMyOlRndU1OeEtvMURTYTF0dWpCTHVaSm5EVWxDY1VBUGxJ | base64 -d
```

#### Output:

```
natas2:TguMNxKo1DSa1tujBLuZJnDUlCcYAPpL
```


## Step 2: Visit the Natas2 Page

### Use browser:

Go to:
[http://natas2.natas.labs.overthewire.org](http://natas2.natas.labs.overthewire.org)
Login using:

* Username: `natas2`
* Password: `TguMNxKo1DSa1tujBLuZJnDUlCcYAPpL`

You’ll see a very plain web page that says something like:

> "There is nothing on this page."



## Step 3: View Page Source

Right-click → "View Page Source" or use curl:

```bash
curl -u natas2:TguMNxKo1DSa1tujBLuZJnDUlCcYAPpL http://natas2.natas.labs.overthewire.org/
```

Check the source. You’ll see this HTML:

```html
<!-- There is nothing on this page -->
<!-- but the page includes some interesting files -->
<link rel="stylesheet" href="files/styles.css">
```

### Hint: `files/` directory

Let’s try to **browse that directory** directly:

Go to:

```
http://natas2.natas.labs.overthewire.org/files/
```

And… boom 💥 — you’ll see an **index listing** (because directory listing is enabled, intentionally for the exercise).

You'll see files like:

* `users.txt`
* `styles.css`

Click or visit:

```
http://natas2.natas.labs.overthewire.org/files/users.txt
```



## ✅ Step 4: Read the users.txt File

You’ll see something like this:

what you have on your screen

<!-- natas3:3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH -->




## Final Result

<!-- * **Username**: `natas3` -->
<!--* **Password**: `3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH`-->

Use it here:
👉 [http://natas3.natas.labs.overthewire.org](http://natas3.natas.labs.overthewire.org)

Looking at the source there is a directory called *files* which is a directory, by openeing it we have a file called *user.txt*

![image](https://github.com/user-attachments/assets/c32ec04e-dc51-4510-842c-ce78db8ba9c7)

![image](https://github.com/user-attachments/assets/3f7b963a-ef06-4e24-9d8f-20d240795504)





## Security Lesson learned

This level teaches:

* **Don't enable directory listing** on sensitive paths.
* Don't leave `.txt` or other unprotected files on the server.
* Always restrict access to `/files/`, `/backup/`, etc.

