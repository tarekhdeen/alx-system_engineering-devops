Here's a step-by-step guide on how to use the SFTP command-line tool to transfer local screenshots to a sandbox environment.

1- Open a Terminal/Command Prompt
2- Type the following command to initiate an SFTP connection to the sandbox environment, replacing username, sandbox.example.com:
"sftp username@sandbox.example.com"
3- Enter your password or provide any required authentication details when prompted.
4- Navigate to the Target Directory on the Sandbox:
"cd /path/to/target/directory"
5- Navigate to the local directory containing your screenshots using the lcd (local change directory) command:
"lcd /path/to/local/screenshots"
6- Use the put command to upload the screenshots to the sandbox:
"put *.png"
7- Close SFTP Session:
"exit"
