1. Check if you have SSH keys on your machine

Run:

ls -al ~/.ssh

If you don’t see files like id_rsa / id_ed25519 and .pub, you need to create a key.

✅ 2. Generate a new SSH key (recommended: ed25519)
ssh-keygen -t ed25519 -C "your_email@example.com"

Press Enter for defaults.

Then start the SSH agent:

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

✅ 3. Add your public key to GitHub

Show your public key:

cat ~/.ssh/id_ed25519.pub

Copy the output, then:

GitHub → Settings → SSH and GPG keys → New SSH key
Paste the key → Save.

✅ 4. Test connection
ssh -T git@github.com

You should see:

Hi <username>! You've successfully authenticated...

If not, tell me what the output says.

✅ 5. Ensure remote URL uses SSH (not HTTPS)

Run:

git remote -v

If you see:

https://github.com/...

change it to SSH:

git remote set-url origin git@github.com:USERNAME/REPO.git

✅ 6. Push again
git push -u origin main
