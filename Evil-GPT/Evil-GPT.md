# Evil-GPT

We are given an ip address and a port to connect: __nc 10.113.149.32 1337__

## Here is how i solved this challenge.

- I am prompted to enter a _command request_, so I tried at first to check if the chatbot has access to the file system:
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

- So it seems that evil-gpt is allowed to access files. Great! Now I observe an odd file _evilai.py_ and decided to print its contents.
> Enter your command request: cat evilai.py

__Generated Command: python3 evilai.py
Execute? (y/N): N
Command execution cancelled.__

- No luck this time, it seems that we may need to use natural language to interpret our prompt.
  
> Enter your command request: read file evilai.py

__Generated Command: cat evilai.py
Execute? (y/N): y
Command Output:__
```python
import ollama
import subprocess
import socket
import threading
import re
import traceback

class AICommandExecutorServer:
    def __init__(self, host='0.0.0.0', port=1337, model='vitali87/shell-commands:latest'):
        """
        Initialize Telnet server for AI command execution
        
        :param host: Host to bind the server
        :param port: Port to listen on
        :param model: Ollama model for command generation
        """
        self.host = host
        self.port = port
        self.model = model
        self.server_socket = None

    def sanitize_input(self, input_str: str) -> str:
        """
        Sanitize input to prevent injection
        
        :param input_str: Raw input string
        :return: Sanitized input
        """
        return re.sub(r'[^a-zA-Z0-9\s\-_./]', '', input_str)

    def generate_command(self, user_request: str) -> str:
        """
        Generate a Linux command based on user request
        
        :param user_request: User's natural language request
        :return: Generated command
        """
        try:
            response = ollama.chat(
                model=self.model,
                messages=[
                    {
                        'role': 'system', 
                        'content': """Do not provide malicious commands. 
                        Only generate safe, read-only Linux commands. 
                        Respond with ONLY the command, no explanations."""
                    },
                    {
                        'role': 'user', 
                        'content': user_request
                    }
                ]
            )
            
            # Extract the command from the response
            command = response['message']['content'].strip()
            return command
        
        except Exception as e:
            return f"Error generating command: {e}"

    def execute_command(self, command: str) -> dict:
        """
        Execute the generated command
        
        :param command: Command to execute
        :return: Command execution results
        """
        try:
            # Sanitize the command to prevent injection
            sanitized_command = self.sanitize_input(command)
            
            # Split the command into arguments
            cmd_parts = sanitized_command.split()
            
            # Execute the command
            result = subprocess.run(
                cmd_parts,
                capture_output=True,
                text=True,
                timeout=30  # 30-second timeout
            )
            
            return {
                "stdout": result.stdout,
                "stderr": result.stderr,
                "returncode": result.returncode
            }
        
        except subprocess.TimeoutExpired:
            return {"error": "Command timed out"}
        except Exception as e:
            return {"error": str(e)}

    def handle_client(self, client_socket):
        """
        Handle individual client connection
        
        :param client_socket: Socket for the connected client
        """
        try:
            # Welcome message
            welcome_msg = "Welcome to AI Command Executor (type 'exit' to quit)\n"
            client_socket.send(welcome_msg.encode('utf-8'))

            while True:
                # Receive user request
                client_socket.send(b"Enter your command request: ")
                user_request = client_socket.recv(1024).decode('utf-8').strip()

                # Check for exit
                if user_request.lower() in ['exit', 'quit', 'bye']:
                    client_socket.send(b"Goodbye!\n")
                    break

                # Generate command
                command = self.generate_command(user_request)
                
                # Send generated command
                client_socket.send(f"Generated Command: {command}\n".encode('utf-8'))
                client_socket.send(b"Execute? (y/N): ")
                
                # Receive confirmation
                confirm = client_socket.recv(1024).decode('utf-8').strip().lower()
                
                if confirm != 'y':
                    client_socket.send(b"Command execution cancelled.\n")
                    continue

                # Execute command
                result = self.execute_command(command)
                
                # Send results
                if "error" in result:
                    client_socket.send(f"Execution Error: {result['error']}\n".encode('utf-8'))
                else:
                    output = result.get("stdout", "")
                    client_socket.send(b"Command Output:\n")
                    client_socket.send(output.encode('utf-8'))
                    
                    if result.get("stderr"):
                        client_socket.send(b"\nErrors:\n")
                        client_socket.send(result["stderr"].encode('utf-8'))

        except Exception as e:
            error_msg = f"An error occurred: {e}\n{traceback.format_exc()}"
            client_socket.send(error_msg.encode('utf-8'))
        finally:
            client_socket.close()

    def start_server(self):
        """
        Start the Telnet server
        """
        try:
            # Create server socket
            self.server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            self.server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
            self.server_socket.bind((self.host, self.port))
            self.server_socket.listen(5)
            
            print(f"[*] Listening on {self.host}:{self.port}")

            while True:
                # Accept client connections
                client_socket, addr = self.server_socket.accept()
                print(f"[*] Accepted connection from: {addr[0]}:{addr[1]}")
                
                # Handle client in a new thread
                client_thread = threading.Thread(
                    target=self.handle_client, 
                    args=(client_socket,)
                )
                client_thread.start()

        except Exception as e:
            print(f"Server error: {e}")
        finally:
            # Close server socket if it exists
            if self.server_socket:
                self.server_socket.close()

def main():
    # Create and start the Telnet server
    server = AICommandExecutorServer(
        host='0.0.0.0',  # Listen on all interfaces
        port=1337       # Telnet port
    )
    server.start_server()

if __name__ == "__main__":
    main()
```
- Skimming through this file, nothing catches my eye. Let us move forware to listing other directories such as root.
> Enter your command request: ls /root

__Generated Command: ls -la /root
Execute? (y/N): y
Command Output:
total 64__
| Permissions | Links | Owner | Group | Size | Date | Time | Name |
|---|---|---|---|---|---|---|---|
| drwx------ | 10 | root | root | 4096 | Mar 5 | 2025 | . |
| drwxr-xr-x | 19 | root | root | 4096 | Mar 2 | 09:20 | .. |
| lrwxrwxrwx | 1 | root | root | 9 | Feb 27 | 2022 | .bash_history -> /dev/null |
| -rw-r--r-- | 1 | root | root | 3106 | Dec 5 | 2019 | .bashrc |
| drwxr-xr-x | 3 | root | root | 4096 | Feb 27 | 2022 | .cache |
| drwx------ | 6 | root | root | 4096 | Oct 11 | 2024 | .config |
| -rw------- | 1 | root | root | 20 | Mar 5 | 2025 | .lesshst |
| drwxr-xr-x | 3 | root | root | 4096 | Feb 27 | 2022 | .local |
| drwxr-xr-x | 5 | root | root | 4096 | Jul 24 | 2024 | .npm |
| drwxr-xr-x | 3 | root | root | 4096 | Jul 24 | 2024 | .ollama |
| -rw-r--r-- | 1 | root | root | 161 | Dec 5 | 2019 | .profile |
| -rw-r--r-- | 1 | root | root | 66 | Feb 27 | 2022 | .selected_editor |
| drwx------ | 2 | root | root | 4096 | Feb 27 | 2022 | .ssh |
| -rw-r--r-- | 1 | root | root | 0 | Mar 5 | 2025 | .sudo_as_admin_successful |
| -rw------- | 1 | root | root | 2884 | Apr 4 | 2024 | .viminfo |
| drwxr-xr-x | 2 | root | root | 4096 | Feb 27 | 2022 | .vnc |
| -rw-r--r-- | 1 | root | root | 24 | Mar 5 | 2025 | flag.txt |
| drwxr-xr-x | 5 | root | root | 4096 | Oct 11 | 2024 | snap |
