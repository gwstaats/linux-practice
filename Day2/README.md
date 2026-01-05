# Day 2 - Linux Foundation: Permissions, Environment, Processes and Logs

## 1. Filesystem Exploration and Permissions

- Used `ls -la` to view hidden files, permission and ownership.
- Observed color codes:
	- Blue = directory
	- Green = executable
	- Cyan = symlink
- Learned why timestamps and ownership matter in servers.

## 2. Environment Variables 

- Listed variables with `env`.
- Checked key variables: `$HOME`, `$PATH`.
- Created temporary variable:
```bash
export MY_VAR="hello_cloud"
echo $MY_VAR
```
- Verified inheritance in subshell:
```bash
echo $MY_VAR
exit
```

## 3. Persistent Environment Variables

- Added variables to ~/.bashrc:
```bash
# practice addition
export MY_VAR="hello_cloud"
```
- Reloaded .bashrc so changes take effect:
```bash
source ~/.bashrc
```
- Confirmed variables persisted across new terminals:
```bash
echo $MY_VAR
```
## 4. Processes & Monitoring

- Viewed all running processes:
```bash
ps aux
```
- Observed user vs root processes, CPU/memory usage, and noted system processes like gjs and systemd.
- Monitored real-time system activity:
```bash
top
```
- Ran a background task for practice:
```bash
sleep 100 &
```
- Checked background jobs:
```bash
jobs
```
- Terminated background task safely using PID:
```bash
ps aux | grep sleep
kill <PID>
jobs
```
- Learned that backgrounding tasks frees the shell for other commands, jobs are shell-local, PIDs are system-wide, safe process termination avoids rebooting servers

## 5. Logs & Troubleshooting

- Viewed recent system logs:
```bash
sudo journalctl -xe | grep -i error | head
```
- Learned to focus on: Patterns vs noise, timestamps to track events, service names to identify source, keywords like error, fail, denied, timeout.
- Key takeaways: Logs are append-only, showing every change or action. `grep` is a magnet for relevant lines. `head` limits output to a manageable snippet. Combining `journalctl`, `grep` and `head` is essential for fast troubleshooting on servers.

