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

# Using Personal Access Tokens

Alternatively, a [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#about-personal-access-tokens) can be used.
After [creating](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-fine-grained-personal-access-token) the token, with the appropriate repo read and write settings, go to gadi and try to push to the remote origin.
You should be prompted first for your username (enter this) then password.
Instead of the password paste the personal access token and you should be good to go!
