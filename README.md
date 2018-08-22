# GPG cheat sheet

### Install GPG on Debian/Ubuntu
```
$ sudo apt install gnupg
```

### Create a key
```
$ gpg --full-generate-key
```

### List keys
```
$ gpg --list-keys
```

### Sending and encrypting a file
1. First, get recipient's public key.
2. Import that key:
    ```
    $ gpg --import recipient.key
    ```
   Check the key was imported successfully by listing the keys. 
3. Export my public key and send it to the recipient (so that they can decrypt the file):
    ```
    $ gpg --export -a "My Name" > myname.key
    ```
4. Encrypt file for recipient:
    ```
    $ gpg -e -u "My Name" -r "Their Name" test.txt
    ```


### Decrypting a file
```
$ gpg -d test.txt.gpg
```

### Encrypting a file for myself
```
$ gpg -e -r "My Name" test.txt
```

### Delete a previously added public key
```
$ gpg --delete-key keyId
```
`keyId` can be found with `gpg --list-keys`

### Delete my own key
1. First, delete the private key:
    ```
    gpg --delete-secret-key keyId
    ```
2. Then delete the public key:
    ```
    gpg --delete-key keyId
    ```