# Windows 10

This is a set of resources and documentation about Windows (Operating System).

## Tips

### If you see something strange in **ipconfig** like `Tunnel adapter Local Area Connection* XX`:

* Open `Device Manager` > Open `View` menu from the top > Check `Show Hidden Devices`
* Expand `Network Adapters` and search for the component that could create this tunnel
* Right click on the component and select `Disable device`

### Group email conversation in Outlook

In `View` page, check `Show as Conversations` (more documentation on [support.office.com/fr-fr](https://support.office.com/fr-fr/article/pr%C3%A9sentation-des-conversations-0eeec76c-f59b-4834-98e6-05cfdfa9fb07)).

### Review credentials

Can be interesting for example to review OneNote credentials.

* Open "Control Panel"
* Click on "User Accounts"
* Manage "Windows Credentials"

### Investigate a problem

* [Record steps to reproduce a problem](https://support.microsoft.com/en-us/windows/record-steps-to-reproduce-a-problem-46582a9b-620f-2e36-00c9-04e25d784e47)

## Commands

Command | Action
------- | ------
`winver` | Get general information on the Windows version and build number
`wmic os get caption` | Get OS caption
`wmic os get osarchitecture` | Get OS architecture

## Applications

### Windows Terminal

[Introducing Windows Terminal](https://devblogs.microsoft.com/commandline/introducing-windows-terminal/) - May 6th, 2019

Can be installed from Microsoft Store.

[Cascadia Code](https://devblogs.microsoft.com/commandline/cascadia-code/) - September 18th, 2019

Can be also available on MacOS with "brew install cask font-cascadia"

## Recipes

* [Disable Windows 10 On Screen Keyboard](https://appuals.com/fix-disable-windows-10-screen-keyboard/)

* Review what is scheduled to be launched at startup
  * Open the registory editor: `regedit`
    * Look at "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run key"

* [Temporarily prevent a driver update from reinstalling in Windows 10](https://support.microsoft.com/en-us/kb/3073930)

* [Have bash in Windows 10](http://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)

* Activate/Reenable Windows lock
  * Open the registory editor: `regedit`
    * Remove "DisableLockWorkStation"
  * Open Local Group Policy Editor: `gpedit.msc`
    * Disable "Remove Lock Computer" (in "Administrative Templates/System/Ctrl+Alt+Del Options")

* [How to turn your Windows 10 computer into a DLNA streaming server](https://www.thewindowsclub.com/turn-windows-10-computer-dlna-streaming-server)

* Troubleshoot memory usage
  * [Top 10 Ways to Fix High CPU/RAM/Memory Usage after Windows 10 Update](https://www.drivethelife.com/windows-10/fix-high-ram-cpu-memory-usage-after-windows-10-update.html)
  * [High Memory Usage on Windows 10](https://www.drivereasy.com/knowledge/high-memory-usage-windows-10-solved/)
  * [How to Fix High CPU/Memory Usage in Windows 10](https://beebom.com/how-fix-high-cpu-memory-usage-windows-10/)
