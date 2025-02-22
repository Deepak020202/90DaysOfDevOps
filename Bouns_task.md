## Bonus Task: Explore SSH Authentication
1. **Generate an SSH Key (if not already set up):**
   - Create an SSH key pair:
     ```bash
     ssh-keygen
     ```
   - Follow the prompts and then locate your public key (typically found at `~/.ssh/id_ed25519.pub`).

2. **Add Your SSH Public Key to GitHub:**  
   - Copy the contents of your public key and add it to your GitHub account under **SSH and GPG keys**.  
     (See [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) for help.)

3. **Switch Your Remote URL to SSH:**  
   - Change the remote URL from HTTPS to SSH:
     ```bash
     git remote set-url origin git@github.com:<your-username>/90DaysOfDevOps.git
     ```

4. **Push Your Branch Using SSH:**  
   - Test the SSH connection by pushing your branch:
     ```bash
     git push origin feature-update
     ```

---

![image](https://github.com/user-attachments/assets/395c75a4-d83e-4b51-b8a4-3910533a1287)

