# Blocklist Manager

The hosts file is a local DNS override used to block domains or redirect websites. (`C:\Windows\System32\drivers\etc\hosts`) A filter get's added via e.g. uBO - filter within the browser -> no system wide blocking.

Preview:

https://github.com/user-attachments/assets/3429692e-2587-440a-b48c-a3b8ba46b149

<ins>Examples:</ins>
```
0.0.0.0 ads.com -> non routable address
127.0.0.1 ads.com -> loopback address

||ads.com^ -> filter (browser)
@@||ads.com^ -> exception
```
First numbers (IP address) is where the domain will be **directed to**, the second (domain name) is the site, which is getting **redirected** (blocked). 

1. [`0.0.0.0`](https://en.wikipedia.org/wiki/0.0.0.0) **blocks/drops** the request instantly - making them "unreachable" (known as being faster than `127.0.01`, but may be incompatible on some systems)
2. [`127.0.0.1`](https://en.wikipedia.org/wiki/localhost) redirects the domain to the **localhost** (your computer) - called "*loopback address*"
3. [`||ads.com^`](https://adblockplus.org/filter-cheatsheet?DE_EXCEPTION=1) blocks the domain - wouldn't block `http://domain.com/redirect/http://ads.com/` -> can't be used within the hosts file
⠀
You should never use all blocklists! This would break most of your applications & slow down your system by a lot. Applying all lists won't give you a better browsing experience! Try to use at least lists as possible. (or use the default preset) Using big lists system wide (hosts file) is also not recommended - if you're planning to use a big list, do that via e.g. uBO (even if the list is compatible with the hosts file). Importing a list will override your current hosts!

## Issues after importing multiple lists?

Open `cmd` and paste `del /f /q C:\Windows\System32\drivers\etc\hosts` into it. If it shows that the DNS client used it, flush your DNS (`ipconfig /flushdns`). Still not? Boot into safemode (`bcdedit /set safeboot minimal`) & remove the hosts file. This may be needed, if importing too many lists.

Default `hosts` content:
```ps
# Copyright (c) 1993-2009 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

# localhost name resolution is handled within DNS itself.
#    127.0.0.1       localhost
#    ::1             localhost
```

## GUI Buttons
The presets are just examples, use lists from the vendor you prefer.
| Button        | Description                                                                                                                                                                                               |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Minimal`     | Preset, which can be used by anyone (hosts/filter).                                                                                                                                                       |
| `Default`     | Default preset, compact size (filter).                                                                                                                                                                    |
| `Maximum`     | For users who want aggressive blocking (filter).                                                                                                                                                          |
| `Import`      | Imports the currently selected lists into the `hosts` file (if compatible).                                                                                                                               |
| `Copy Links`  | Copies URLs of all selected lists. Add these links to the custom filter lists:<br>![ubolinks](https://github.com/5Noxi/Blocklist-Modification/blob/main/ubolinks.png?raw=true)       |
| `Restore`     | Imports the backup from: `C:\Windows\System32\drivers\etc\hosts.noverse`.                                                                                                                                 |
| `Open File`   | Opens the file: `C:\Windows\System32\drivers\etc\hosts`.                                                                                                                                                   |

## Additional features:
- Click on the category name (blue) to open the source link
- Adjust the window size, to increase the size of the hosts/log box
- `hosts` preview refreshes itself automatically
- You can edit the hosts file via the panel in the GUI (doesn't create a backup)

More lists/information:</ins>
> https://github.com/gorhill/uBlock/wiki/  
> https://github.com/yokoffing/filterlists  
> https://adblockplus.org/filter-cheatsheet  
> https://github.com/DandelionSprout/adfilt  
> https://github.com/uBlockOrigin/uAssets  
> https://filterlists.com/  
> https://pi-hole.net/  
> https://sefinek.net/blocklist-generator  
> https://github.com/pixeltris/TwitchAdSolutions  
> https://learn.microsoft.com/en-us/windows/powertoys/hosts-file-editor  
> https://pyfunceble.github.io/#/  
> https://learn.microsoft.com/en-us/windows/privacy/windows-11-endpoints-non-enterprise-editions  
> https://learn.microsoft.com/en-us/windows/privacy/manage-windows-11-endpoints  
