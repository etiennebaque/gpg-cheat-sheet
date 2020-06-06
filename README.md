# GPG cheat sheet

### Install GPG on Debian/Ubuntu

```bash
$ sudo apt install gnupg
```

### Create a key

```bash
$ gpg --full-generate-key
```

### List keys

```bash
$ gpg --list-keys --fingerprint
```

### Export my public key

```bash
$ gpg --export -a "My Name" > myname.asc
```

### Export my private key

```bash
$ gpg --armor --export-secret-keys "My Name" > myname.asc
```

### Sending and encrypting a file

1. First, get recipient's public key and send them mine.
1. Import their key:
   ```bash
   $ gpg --import recipient.asc
   ```
   Check that the key was imported successfully by listing the keys available on my machine.
1. Encrypt file for recipient:
   ```bash
   $ gpg -e -u "My Name" -r "Their Name" test.txt
   ```

### Decrypting a file

```bash
$ gpg -d test.txt.gpg
```

### Encrypting a file for myself

```bash
$ gpg -e -r "My Name" test.txt
```

### Delete a previously added public key

```bash
$ gpg --delete-key keyId
```

`keyId` can be found with `gpg --list-keys`

### Delete my own key

1. First, delete the private key:
   ```bash
   gpg --delete-secret-key keyId
   ```
1. Then delete the public key:
   ```bash
    gpg --delete-key keyId
   ```
