# How to Add a Deploy Key and Push from Gadi

  

#### 1. Create a Public Key

```bash
eval "$(ssh-agent -s)"
ssh-add -l -E sha256
ssh-add
```

Returns:
```bash
Identity added: /home/561/ic0706/.ssh/id_ed25519 (i.conde@unsw.edu.au)
```


Hopefully this will have added a public key. We need the exact key name for this, so we will need to look at the file.


Go to the directory where the key was added, and list the contents:


```bash
cd ~/.ssh
ls -a
```


The public key will end in `.pub`. We need to open it to get the key name:

```bash
vim id_ed25519.pub
```

The public key file should look like:  

```bash
ssh-ed25519 AAAC3NzaC1lZDI1NTE5AAAAICdFviaLqaoeu2DtGvhcbGEwa8kixKGQETye8/qpQRgB i.conde@unsw.edu.au
```

This:

```bash
ssh-ed25519 AAAC3NzaC1lZDI1NTE5AAAAICdFviaLqaoeu2DtGvhcbGEwa8kixKGQETye8/qpQRgB
```

  

is the public key that will be needed.

#### 2. Add a Deploy Key to the Repo

In GitHub, go to the repo that you want to commit to, and click on **Settings**.

Under **Security**, there is a **Deploy keys** tab. Click **Add deploy key**.

You’ll be prompted for a name and key. The name can be whatever you like; the key should be the public key.

#### 3. Push from Gadi

In the Gadi terminal, for some reason it didn’t accept pushing to `origin/main`, so I created a new branch `origin/master` and then made that branch the default.

```bash
git push -u origin master
```
