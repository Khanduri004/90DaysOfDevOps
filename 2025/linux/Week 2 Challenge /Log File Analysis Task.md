### **Task 3️⃣ Log File Analysis with AWK, Grep & Sed**
Logs are crucial in DevOps! 
Log analysis in Linux is crucial for DevOps troubleshooting for several reasons, as it allows teams to monitor, diagnose, and resolve issues quickly, 
ensuring that applications and infrastructure run smoothly.
In this we’ll analyze logs using the **Linux_2k.log** file from **LogHub** ([GitHub Repo](https://github.com/logpai/loghub/blob/master/Linux/Linux_2k.log)).

- **Task:**  
  - **Download the log file** from the repository.
  - **Extract insights using commands:**
    - Use `grep` to find all occurrences of the word **"error"**.
    - Use `awk` to extract **timestamps and log levels**.
    - Use `sed` to replace all IP addresses with **[REDACTED]** for security.
  - **Bonus:** Find the most frequent log entry using `awk` or `sort | uniq -c | sort -nr | head -10`.
 
  - ## Commands Used

To perform this task, use the following commands:

```bash
# Download the log file
wget https://raw.githubusercontent.com/logpai/loghub/master/Linux/Linux_2k.log -O Linux_2k.log

# Find all occurrences of "error"
grep -i "error" Linux_2k.log > error_logs.txt

# Extract timestamps and log levels
awk '{print $1, $2, $3, $6}' Linux_2k.log > timestamps_logs.txt

# Mask all IP addresses for security
sed -E 's/[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+/[REDACTED]/g' Linux_2k.log > masked_logs.txt

# Find the most frequent log entry
awk '{print $6}' Linux_2k.log | sort | uniq -c | sort -nr | head -10 > frequent_logs.txt
```

By leveraging log analysis tools and practices, DevOps teams can improve uptime, reduce time-to-resolution, and enhance 
the performance and security of their infrastructure.

