# "Cheat Sheet" of common linux commands to debug

## 1. Troubleshooting & Logs

When an application isn't working, these are your first tools:

- `tail -f [filename]` : Used to watch logs in real-time.    

- `grep -i "error" [filename]` : Used to search for specific keywords like "error" or "failed" within a file.    

- `top` or `htop` : To check CPU and RAM usage to see if a process is crashing the server.

---

## 2. Networking & Connectivity

To find why a service can't talk to a database:

- `curl -v [URL]` : Checks if a web service is reachable and shows the headers.

- `netstat -tuln` : Shows all active ports to see if your application (like Jenkins or a Flask API) is actually listening.

- `nslookup [domain]` : Used to verify if DNS is working correctly.

---

## 3. File & Permission Management

Crucial for Least Privilege and security:

- `chmod` : To change file permissions (e.g., making a script executable).

- `chown` : To change who owns a file or folder (important for Jenkins access).

- `df -h` : To check if your disk is full (a common reason why builds fail).

---

## 4. Critical Scenario: "The server is slow. What do you do?"

- Check Resources: Run `top` to see if a process is hogging the CPU.

- Check Disk Space: Run `df -h` to see if the logs have filled up the storage.

- Check Logs: Use `tail` on the application logs to see if it's stuck in a loop.

---
