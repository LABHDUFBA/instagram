## Instagram username availability checker.

It pretty much checks if a username is claimed on instagram or not. 

**Code:**

```
import requests

usernames = [line.strip() for line in open("usernames.txt")]

for username in usernames:
    z = requests.get(f"https://instagram.com/{username}")
    if z.status_code == 200:
        print(f"{username} is taken")
        with open("claimed.txt", 'a') as f:
            f.write(f"{username}\n")
    elif z.status_code == 404:
        print(f"{username} is not taken")
        with open("not_claimed.txt", 'a') as f:
            f.write(f"{username}\n")
    else:
        print(f"Your IP might be temp blocked. [Status code {z.status_code}]")
```

HOW TO USE IT:  
Save the script in a folder and call it

Code:

```
main.py
```

Put the usernames that you want to check in a file called

Code:

```
usernames.txt
```

Make sure that they are only 1 per line, so like this:  

Code:

```
Username1
Username2
Username3
...
```

After you've created the usernames.txt and the main.py file you can just execute the script by double-clicking the main.py file.  
(For some people double-clicking the file might not work, just open a cmd in that folder and type

Code:

```
python main.py
```
