# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
Cracked Passwords from Hash File
<img width="1600" height="899" alt="dff-1" src="https://github.com/user-attachments/assets/2d380f25-5e17-4121-af28-c29a479cf696" />
<img width="1600" height="899" alt="dff-2" src="https://github.com/user-attachments/assets/b6333262-6e28-4285-a26d-996ae32652e2" />
<img width="1600" height="899" alt="dff-3" src="https://github.com/user-attachments/assets/93404670-ad9b-47fd-88f2-3cfb43148179" />
<img width="1600" height="899" alt="dff-4" src="https://github.com/user-attachments/assets/4733803e-f1fe-4fe8-9373-ad77787e47c3" />
<img width="1600" height="898" alt="dff-5" src="https://github.com/user-attachments/assets/9df315e9-a85e-4737-8dd6-8b3dcc6d0d0c" />
<img width="1917" height="1072" alt="dff-6" src="https://github.com/user-attachments/assets/9f3ea624-9f20-40c4-a85e-d4216f0d90a9" />
<img width="1600" height="900" alt="dff-7" src="https://github.com/user-attachments/assets/e6682a0b-d8de-4ef1-bea2-5040355a34fd" />









## RESULT:
The password hashes were successfully cracked using John the Ripper.

