# 01 Installing the Domain Controller

1. Use `Sconfig` to:
	- Change the hostname
	- Change the IP address to static
	- Change the DNS server to our own IP address


```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools 
Install-ADDSForest
```

```shell
Get-NetIPAddress
```

# 02 Managing the Domain Controller from our Management Client Machine:

1. Specifying a $dc Variable to capture our Powershell Remoting Session

	`$dc = New-PSSession -ComputerName "IPAddress -Credential (Get-Credential)"`

2. Or do it Manually through the steps below	
	```
	New-PSSession -ComputerName "IPAddress" -Credential (Get-Credential)
	Enter-PSSession 1 OR Enter-PSSession $dc
	```
 
# 03 joining the Workstation to the domain

```shell
Get-DnsClientServerAddress #Note down the Interface Index
Set-DNSClientServerAddress "InterfaceIndex" –ServerAddresses "ServerAddress" 
Add-Computer -DomainName xyz.com -Credential xyz\Administrator -Force -Restart
```
