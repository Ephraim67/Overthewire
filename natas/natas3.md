## 🧪 Step-by-Step:

### 🔍 Command:

```bash
curl -u natas3:3gqisGdR0pjm6tpkDKdIWO2hSvchLeYH http://natas3.natas.labs.overthewire.org/robots.txt
```

### If it exists, you’ll see output like:

![image](https://github.com/user-attachments/assets/45a756aa-1f82-4f57-ae01-6aa3a1bebc93)


```
User-agent: *
Disallow: /s3cr3t/
```

This would confirm the existence of a hidden directory — which in this level is:

```
/s3cr3t/
```

### Then use burpsuite to get the contents of the file:

![image](https://github.com/user-attachments/assets/3e1768b8-3c44-462e-93c3-fa8287691dd3)


## Security Lesson

This is the trap:

* Developers think hiding something in `robots.txt` keeps it "secret."
* But it literally advertises the location of hidden paths to **anyone who looks**.

This is called **"Security through obscurity"** — and it's weak.





When doing recon on a target (CTF or real):

1. Check `/robots.txt`
2. Check `/sitemap.xml`
3. Check for `.git/`, `.env`, `/backup/`, `/admin/`, etc.
4. Check for open directory listings
5. Bruteforce hidden paths (`ffuf`, `dirb`, `gobuster`)

| Action                  | Command                                                                     |
| ----------------------- | --------------------------------------------------------------------------- |
| Check for hidden paths  | `curl -u natas3:<pass> http://natas3.natas.labs.overthewire.org/robots.txt` |
| Visit disclosed path    | `/s3cr3t/`                                                                  |
| Grab password from file | `/s3cr3t/users.txt`                                                         |

natas4:QryZXc2e0zahULdHrtHxzyYkj59kUxLQ
