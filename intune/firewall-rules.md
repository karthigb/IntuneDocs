# Windows Defender Firewall Rules

Configure Windows Defender Firewall rules straight from the Intune console. To get started, open the *Device Configuration* workload,then create a new profile. Choose *Windows 10* as the platform, and *Endpoint Protection* as the profile type. Select the Windows Defender Firewall chevron. Add a firewall rule to this new *Endpoint Protection* profile using the *Add* button at the bottom of the blade.

![Firewall rules in device configuration](/media/firewallrules.PNG)

**Important!** A single *Endpoint Protection* profile may contain up to a maximum of 150 firewall rules. If a client device requires more than 150 rules, then multiple profiles must be assigned to it.

## Firewall rule components

**Name**

The name of the rule in Intune.

**Description**

The description of the rule.

**Direction**

Specifies whether the rule applies to inbound or outbound network traffic. If left Not configured, the rule defaults to outbound traffic.

**Action**

Specifies whether this rule should block or allow network traffic. If left Not configured, the rule defaults to allow traffic.

**Network type**

Specifies the network type to which the rule belongs: Domain, Private, or Public. If left Not configured, the rule applies to all network types.

**Application**

Control connections for an app or program. Apps and programs can be specified either file path, or package family name.

The file path of an app is simply its location on the client device. For example, *C:\Windows\System\Notepad.exe*. [Learn more](https://aka.ms/intunefirewallfilepathrule)

Package family names can be retrieved by running the *Get-AppxPackage* command from PowerShell. [Learn more](https://aka.ms/AppXPackageNameFromPowerShell)

Windows service short names are used in cases when a service, not an application, is sending or receiving traffic. [Learn more](https://aka.ms/intunefirewallservicenamerule)

**Protocol**

Select the protocol for this port rule. Transport layer protocols - TCP and UDP – allow you to specify ports or port ranges. For custom protocols, enter a number between 0 and 255 representing the IP protocol.

Default is Any. [Learn more](https://aka.ms/intunefirewallprotocolrule)

**Local ports**

Comma separated list of ranges. For example, *100-120*,*200*,*300-320*.

Default is All. [Learn more](https://aka.ms/intunefirewalllocalportrule)

**Remote ports**

Comma separated list of ranges. For example, *100-120*,*200*,*300-320*.

Default is All. [Learn more](https://aka.ms/intunefirewallremoteportrule)

**Local addresses**

Comma separated list of local addresses covered by the rule. Valid tokens include:

+ *&#42;* indicates any local address. If present, this must be the only token included.
+ A subnet can be specified using either the subnet mask or network prefix notation. If neither a subnet mask not a network prefix is specified, the subnet mask defaults to 255.255.255.255.
+ A valid IPv6 address.
+ An IPv4 address range in the format of "start address - end address" with no spaces included.
+ An IPv6 address range in the format of "start address - end address" with no spaces included.

Default is Any address. [Learn more](https://aka.ms/intunefirewalllocaladdressrule)

**Remote addresses**

List of comma separated tokens specifying the remote addresses covered by the rule. Tokens are case insensitive. Valid tokens include:

+ *&#42;* indicates any remote address. If present, this must be the only token included.
+ Defaultgateway
+ DHCP
+ DNS
+ WINS
+ Intranet  (supported on Windows versions 1809+)
+ RmtIntranet (supported on Windows versions 1809+)
+ Internet (supported on Windows versions 1809+)
+ Ply2Renders (supported on Windows versions 1809+)
+ LocalSubnet indicates any local address on the local subnet.
+ A subnet can be specified using either the subnet mask or network prefix notation. If neither a subnet mask not a network prefix is specified, the subnet mask defaults to 255.255.255.255.
+ A valid IPv6 address.
+ An IPv4 address range in the format of "start address - end address" with no spaces included.
+ An IPv6 address range in the format of "start address - end address" with no spaces included.

Default is Any address. [Learn more](https://aka.ms/intunefirewallremoteaddressrule)

**Edge traversal**

Indicates whether edge traversal is enabled or disabled for this rule.

The EdgeTraversal setting indicates that specific inbound traffic is allowed to tunnel through NATs and other edge devices using the Teredo tunneling technology. In order for this setting to work correctly, the application or service with the inbound firewall rule needs to support IPv6. The primary application of this setting allows listeners on the host to be globally addressable through a Teredo IPv6 address.

New rules have the EdgeTraversal property disabled by default. [Learn more](https://aka.ms/intunefirewalledgetraversal)

**Authorized users**

Specifies the list of authorized local users for this rule. **A list of authorized users cannot be specified if the rule being authored is targeting a Windows service.**

Default is all users. [Learn more](https://aka.ms/intunefirewallauthorizedusers)
