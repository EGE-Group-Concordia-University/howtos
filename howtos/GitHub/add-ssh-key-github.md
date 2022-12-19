# Adding a new SSH key to your GitHub account

This is a simplified how-to on how to setup authentication using SSH key to GitHub. 
The full documentation is available on the official GitHub [documentation](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).

This how-to gives specific commands for our JupyterHub environment. This is a one time setup that needs to be done.

## Generate new SSH key pair
Open a terminal using the JupyterLab launcher and execute the following command substituting in your GitHub email address:
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```
The utility will prompt you to select a location for the keys that will be generated. 
By default, the keys will be stored in the ```~/.ssh``` directory within your user’s home directory.
The private key will be called ```id_ed25519``` and the associated public key will be called ```id_ed25519.pub```.

If you had previously generated an SSH key pair, you will be asked if you want to overwrite it.
If you choose to overwrite the key on disk, you will not be able to authenticate using the previous key anymore.

Next, you will be prompted to enter a passphrase for the key. As we need a password less access to GitHub, provide an empty passphrase by simply pressing the ```ENTER``` key.
```
Output
Your identification has been saved in /home/username/.ssh/id_ed25519.
Your public key has been saved in /home/username/.ssh/id_ed25519.pub.
The key fingerprint is:
ssh-ed25519:CAjsV9M/tt5skazroTc1ZRGCBz+kGtYUIPhRvvZJYBs your_email@example.com
The key's randomart image is:
+---[RSA 3072]----+
|o   ..oo.++o ..  |
| o o +o.o.+...   |
|. . + oE.o.o  .  |
| . . oo.B+  .o   |
|  .   .=S.+ +    |
|      . o..*     |
|        .+= o    |
|        .=.+     |
|       .oo+      |
+----[SHA256]-----+
```

As your key is not protected by a passphrase, it is important to have appropriate file permissions of the generated keys.
The default permissions (```id_ed25519``` only user has read/write access 
and ```id_ed25519.pub``` user has read/write access and group and world has read access) 
created by ```ssh-keygen``` are the ones to use and should not be changed.

You can verify the file permissions with
```
ls ~/.ssh -l
```
```
Output
-rw------- 1 username group 2602 Sep  9 19:53 id_ed25519 
-rw-r--r-- 1 username group  571 Sep  9 19:53 id_ed25519.pub
```

## Adding your SSH key to the ssh-agent
In a terminal in JupyterLab run (make sure your shell is `bash`. You can always start a `bash` shel by first runnign the command `bash` in your terminal):
```
eval "$(ssh-agent -s)"
```
followed by
```
ssh-add ~/.ssh/id_ed25519
```

## Adding a new SSH key to your GitHub account
First we need to copy the public key. In a terminal in JupyterLab run
```
cat ~/.ssh/id_ed25519.pub
```
This will display your public key to the screen (including your email adress). Copy the full content (including the email address) to your clipboard.

The copied text needs to be pasted in your GitHub settings. For this (see [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) for more info):

1. In the upper-right corner of GitHub, click your profile photo, then click Settings.

2. In the "Access" section of the sidebar, click SSH and GPG keys.

3. Click New SSH key or Add SSH key.

4. In the "Title" field, add a descriptive label for the new key. This can be anything you choose.

5. Select the type of key: authentication

6. Paste your key into the "Key" field.

7. Click Add SSH key. 

## Check connectivty to GitHub
Check if you can connect to GitHub using ssh by runing the following command in a terminal in JupyerLab
```
ssh -T git@github.com
```
You may see a warning like this:
```
The authenticity of host 'github.com (IP ADDRESS)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)?
```
Answer by yes.

Note: this checking step is required as it will force to add github.com to the trusted hosts on your JupyterHub account.
