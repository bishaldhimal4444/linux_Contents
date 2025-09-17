# Access the Remote Command Line with SSH.
1. ssh into a hosta remote server by using the same useranme as the current local user:
```
ssh hosta
```
2. ssh into the hosta remote server with the developer2 username:
```
ssh developer2@hosta
```

# ssh host keys:
- The host key is a cryptographic key pairs used by an ssh server to identify itself to clients.
- when a client connect to an ssh server for the first time, the server sends its public_key(host_key) to the client.
- If the client has a copy of the key, then the ssh command compares the key from the known_hosts_server files to the key that it received.

#### Host key Storage:
1. client side:
  - ~/.ssh/known_hosts (per users)
  - /etc/ssh/ssh_known_hosts (system_wide)

2. server side: /etc/ssh

## Strict Host Key Checking:
- The StrictHostKeyChecking setting in SSH controls how the client handles the server's host key during a connection.
- It determines whether the cilent should automatically accept a new or changed host key.
  Options:
    - yes: strictly check the host key. If the host key is not in ~/.ssh/known_hosts or has changed, the connection is refused.
    - no: automatically accept new host keys. If a  key has changed, the client will issue a warning but allow the connection.
    - ask (default): prompt the user to confirm adding a new host key or to proceed when the key changes.

  - The StrictHostKeyChecking parameter is set in the user-specific: ~/.ssh/config or /etc/ssh/ssh_config (system-wide)
 
Practical Commands: 
```
ssh-keyscan -H hostname >> ~/.ssh/known_hosts
ssh -o StrictHostKeyChecking=no user@hostname
ssh -v user@hostname
```

## Configure SSH key-based Authentication:
Configure your account or passwordless access to ssh servers that enabled key_based authentication, which is based on public key encryption (PKI).
1. SSH keys Generation
   ```
   ssh-keygen
   ssh-keygen -t rsa -b 2048
   ssh-keygen -t rsa -b 2048 -f ~/.ssh/<key_with_pass>
   ```
2. Non-interactive Authentication with key Manager:
   - if you encrypt your private key with a passphrase, then you must enter the passphrase each time that you use the private key for authentication.
   - However, you can configure the ssh-agent key manager to cache passphrases.
   - you must start the ssh_agent program manually for each session, using following cmd:
     ```
     eval $(ssh_agent)
     ```
     Above, cmd sets environment variable to manually load the private key passphrase to the key manager by using below cmd:
     ```
     ssh-add
     ssh-addd .ssh/key_with_pass
     ```
     Output: Enter passphrase for .ssh/key_with_pass:
3. Basic SSH Connection Troubleshooting:
   ```
   ssh -v user@remotehost
   ```
   verbosity levels: -v, -vv and -vvv options
