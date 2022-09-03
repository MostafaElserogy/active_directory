# 01 Installing the Domain Controller

1. Use `Sconfig` to:
	- Change the hostname
	- Change the IP address to static
	- Change the DNS server to our own IP address

	```shell
	Install-WindowsFeature AD-Domain-Services -IncludeManagementTools 

	```