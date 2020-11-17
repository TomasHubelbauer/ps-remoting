# PowerShell Remoting

On the remote computer:

```powershell
Enable-PSRemoting
$env:ComputerName
$env:UserName
```

On the local computer:

```powershell
# Set $computerName and $userName based on the command on the remote computer
Test-WsMan $computerName
Invoke-Command -ComputerName $computerName -ScriptBlock { echo "Hello, World" } -credential $userName
```

I get this:

```
OpenError: [$computerName] Connecting to remote server $computerName failed with the following error message:
The WinRM client cannot process the request.

If the authentication scheme is different from Kerberos, or if the client computer is not joined to a domain,
then HTTPS transport must be used or the destination machine must be added to the TrustedHosts configuration setting.

Use winrm.cmd to configure TrustedHosts.
Note that computers in the TrustedHosts list might not be authenticated. You can get more information about that
by running the following command: winrm help config.

For more information, see the about_Remote_Troubleshooting Help topic.
```

## To-Do

### Figure out the problem and capture the solution

Might it be that I'm testing with Windows Sandbox for the remote computer? So essentially talking to self?
Or is the `-credential` supposed to be the one from the local computer? I should probably read the error
message.
