# Evil-GPT

We are given an ip address and a port to connect: __nc 10.113.149.32 1337__

## Here is how i solved this challenge.

I am prompted to enter a _command request_, so I tried at first to check if the chatbot has access to the file system:
> Enter your command request: ls

__enerated Command: ls -la
Execute? (y/N): y
Command Output:
total 172__
| Permissions | Links | Owner | Group | Size | Date | Time | Name |
|---|---|---|---|---|---|---|---|
| drwxr-xr-x | 27 | ubuntu | ubuntu | 4096 | Mar 2 | 09:20 | . |
| drwxr-xr-x | 3 | root | root | 4096 | Mar 5 | 2025 | .. |
| -rw------- | 1 | ubuntu | ubuntu | 3275 | Mar 2 | 09:20 | .Xauthority |
| lrwxrwxrwx | 1 | ubuntu | ubuntu | 9 | Feb 27 | 2022 | .bash_history -> /dev/null |
| -rw-r--r-- | 1 | ubuntu | ubuntu | 220 | Feb 25 | 2020 | .bash_logout |
| -rw-r--r-- | 1 | ubuntu | ubuntu | 3968 | Jul 23 | 2024 | .bashrc |
| drwx------ | 20 | ubuntu | ubuntu | 4096 | Oct 11 | 2024 | .cache |
| drwx------ | 28 | ubuntu | ubuntu | 4096 | Jul 24 | 2024 | .config |
| drwx------ | 3 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | .dbus |
| drwx------ | 3 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | .gnupg |
| drwxrwxr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | .icons |
| -rw------- | 1 | ubuntu | ubuntu | 20 | Mar 5 | 2025 | .lesshst |
| drwx------ | 7 | ubuntu | ubuntu | 4096 | Mar 5 | 2025 | .local |
| drwx------ | 4 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | .mozilla |
| drwxrwxr-x | 5 | ubuntu | ubuntu | 4096 | Jul 23 | 2024 | .npm |
| drwxrwxr-x | 8 | ubuntu | ubuntu | 4096 | Jul 23 | 2024 | .nvm |
| drwxr-xr-x | 3 | ubuntu | ubuntu | 4096 | Mar 5 | 2025 | .ollama |
| drwx------ | 3 | ubuntu | ubuntu | 4096 | Apr 4 | 2024 | .pki |
| -rw-r--r-- | 1 | ubuntu | ubuntu | 807 | Feb 25 | 2020 | .profile |
| -rw------- | 1 | ubuntu | ubuntu | 3567 | Oct 10 | 2024 | .python_history |
| -rw-rw-r-- | 1 | ubuntu | ubuntu | 66 | Feb 27 | 2022 | .selected_editor |
| drwx------ | 2 | ubuntu | ubuntu | 4096 | Apr 5 | 2024 | .ssh |
| -rw-r--r-- | 1 | ubuntu | ubuntu | 0 | Feb 27 | 2022 | .sudo_as_admin_successful |
| drwxrwxr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | .themes |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Apr 5 | 2024 | .vim |
| -rw------- | 1 | ubuntu | ubuntu | 14039 | Apr 5 | 2024 | .viminfo |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Mar 2 | 09:20 | .vnc |
| -rw-rw-r-- | 1 | ubuntu | ubuntu | 290 | Oct 8 | 2024 | .wget-hsts |
| -rw------- | 1 | ubuntu | ubuntu | 5833 | Feb 27 | 2022 | .xsession-errors |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | Desktop |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | Documents |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Apr 4 | 2024 | Downloads |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | Music |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | Pictures |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | Public |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | Templates |
| drwxr-xr-x | 2 | ubuntu | ubuntu | 4096 | Feb 27 | 2022 | Videos |
| -rw-rw-r-- | 1 | ubuntu | ubuntu | 6595 | Mar 5 | 2025 | evilai.py |
| drwxrwxr-x | 4 | ubuntu | ubuntu | 4096 | Apr 4 | 2024 | packages |
| drwxrwxr-x | 3 | ubuntu | ubuntu | 4096 | Apr 4 | 2024 | proxy |
