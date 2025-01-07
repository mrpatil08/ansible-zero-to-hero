# How to setup Passwordless Authentication

## EC2 Instances

### Using Public Key

```
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
```

- ssh-copy-id: This is the command used to copy your public key to a remote machine.
- -f: This flag forces the copying of keys, which can be useful if you have keys already set up and want to overwrite them.
- "-o IdentityFile <PATH TO PEM FILE>": This option specifies the identity file (private key) to use for the connection. The -o flag passes this option to the underlying ssh command.
- ubuntu@<INSTANCE-IP>: This is the username (ubuntu) and the IP address of the remote server you want to access.

### Using Password 

- Go to the file `/etc/ssh/sshd_config.d/60-cloudimg-settings.conf`
- Update `PasswordAuthentication yes`
- Restart SSH -> `sudo systemctl restart ssh`

#### Run the below command for Passwordless Authentication using Password
```
ssh-copy-id username@<server-ip>
```

- If anyone ran into the issue of /usr/bin/ssh-copy-id: ERROR: No identities found while setting up passwordless authentication via public key
- Make sure you have a PEM file in the default location (~/.ssh/id_rsa) or specify
- If not, create public key pair using "ssh-keygen"

bash
root@DJQW8473:/mnt/c/WINDOWS/system32# ssh-keygen
Generating public/private ed25519 key pair.
Enter file in which to save the key (/root/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /root/.ssh/id_ed25519
Your public key has been saved in /root/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:/VhUQtn1VknIBHAVGs8Ep3aZ78TFzUiw6nar2LGQkic root@DJQW8473
The key's randomart image is:
+--[ED25519 256]--+
|         ..*XX*o+|
|          . XB+=+|
|           +o*. B|
|         ..o. o..|
|        S o .  + |
|       . o +  o  |
|      E + = o  . |
|       + = + .   |
|        . +..    |
+----[SHA256]-----+

