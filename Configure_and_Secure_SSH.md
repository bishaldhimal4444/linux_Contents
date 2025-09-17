# Access the Remote Command Line with SSH.
1. ssh into a hosta remote server by using the same useranme as the current local user:
2. ssh into the hosta remote server with the developer2 username:

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
- 
