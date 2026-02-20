# For windows

✅ Create SSH key on Windows (PowerShell method)
1. Open PowerShell

Press Win + S → type “PowerShell” → Enter

2. Generate SSH key

Run:

ssh-keygen -t ed25519 -C "your_email@example.com"

Press Enter for default location:

C:\Users\YourUsername\.ssh\id_ed25519

(Optional) set a passphrase or press Enter.

You now have:

private key → id_ed25519
public key  → id_ed25519.pub
3. Copy the public key to clipboard

Run:

Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | Set-Clipboard

Now your public key is copied.

Paste it anywhere (GitHub, server, etc).

✅ View public key manually (if needed)
notepad $env:USERPROFILE\.ssh\id_ed25519.pub

Copy the full line starting with:

ssh-ed25519 AAAA...
Quick check (optional)
ls ~/.ssh

You should see:

id_ed25519
id_ed25519.pub

---

Windows uses the same SSH config file, just in a different path.

✅ Windows equivalent of ~/.ssh/config

On Windows:

C:\Users\YourUsername\.ssh\config

(~ on Windows = C:\Users\YourUsername)

✅ Create / edit the config file
1. Open PowerShell
2. Open config file (creates if missing)
notepad $env:USERPROFILE\.ssh\config
3. Paste your config

Change the path to Windows format:

Host boostrun
    HostName 103.196.86.31
    User demo
    IdentityFile C:\Users\YourUsername\.ssh\boostrun_id_ed25519

Or you can use forward slashes:

IdentityFile ~/.ssh/boostrun_id_ed25519

(OpenSSH on Windows supports this.)

Save and close.

✅ Use it

Now you can connect with:

ssh boostrun
Quick verify SSH is installed (if unsure)
ssh -V

If it prints a version → you're good.
