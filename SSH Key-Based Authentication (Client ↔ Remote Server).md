# SSH Key-Based Authentication (Client ↔ Remote Server) – Simple Explanation


## What Is SSH?
SSH (Secure Shell) is used to **securely connect from a client machine to a remote server**.

Example:
- Client: your laptop / Jenkins server
- Remote server: EC2 / VM / Linux server

---

## SSH Uses Two Keys
SSH key-based authentication uses **two keys** that are mathematically related:

- Private Key
- Public Key

---

## Private Key (Client Side)

### What Is It?
- Secret key
- Generated on the **client**
- Must NEVER be shared

### Where It Lives?
- On the client machine only
- Example path:
~/.ssh/id_rsa

### What Is It Used For?
- To prove the client’s identity during SSH login
- Used to respond to the server’s challenge

---

## Public Key (Copied to Remote Server)

### What Is It?
- Safe to share
- Generated along with the private key

### Where Is It Stored?
- On the **remote server**
- Inside:
~/.ssh/authorized_keys

### What Is It Used For?
- Remote server uses it to verify the client

---

## IMPORTANT RULE (MEMORIZE THIS)

Client keeps the **private key**  
Remote server stores the **client’s public key**

---

## Correct SSH Setup (Step-by-Step)

### Step 1: Generate Keys on the CLIENT
Keys are created on the client machine:
- Private key → stays on client
- Public key → copied to server

---

### Step 2: Copy CLIENT’S Public Key to REMOTE SERVER
The client’s public key is added to:
~/.ssh/authorized_keys (on remote server)

This tells the remote server:
“This client is allowed to log in.”

---

### Step 3: Client Tries to Connect
From the client:
ssh user@remote_server_ip

---

### Step 4: Client Uses Its PRIVATE Key
- Client proves its identity using the private key
- Private key NEVER travels over the network

---

### Step 5: Remote Server Verifies Using STORED PUBLIC KEY
- Remote server checks the **client’s public key** stored in authorized_keys
- It compares the response from the client

IMPORTANT:
- Remote server does NOT use its own public key for verification
- It uses the **client’s public key**

---

### Step 6: Result
- If keys match → Login allowed
- If keys do not match → Login denied

Error example:
Permission denied (publickey)

---

## Common Misunderstanding (Clarified)

❌ Remote server checks login using its own public key  
✅ Remote server checks login using the **client’s public key stored on it**

---

## Very Simple Analogy

- Client = Person
- Private key = Personal signature
- Public key on server = Signature sample kept for verification

Server compares:
- Signature made now
- With the stored signature sample

If it matches → access allowed

---

## Interview-Ready One-Line Answer
“The client generates an SSH key pair and copies its public key to the remote server. During login, the client proves its identity using the private key, and the remote server verifies it using the client’s public key stored in authorized_keys.”

---

## Key Takeaways
- Keys are generated on the client
- Private key stays on client
- Client’s public key is copied to remote server
- Remote server verifies using client’s public key
- Remote server’s own keys are not used for login verification
