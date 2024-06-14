---
tags: computers
---

## Teredo is unable to qualify

So you’re trying to play Forza on Windows 10 or whatever and the Xbox Live Networking app is giving you this error:

```
NAT Type: Teredo is unable to qualify.

Server Connectivity: Blocked
```

There’s a million fixes online and the error has existed for years. Hope this saves you the hours of troubleshooting I had to do. I fixed the error by forcing the correct settings via group policy.

Run the local group policy editor. (Windows Key + R, type in gpedit.msc)

Computer Configuration > Administrative Templates > All Settings

Find these settings and double click it to edit. Remember to hit apply.

```
“Set Teredo Client Port” set: Enabled, port 0

“Set Teredo Default Qualified” set: Enabled, Enabled State

“Set Teredo Refresh State” set: Enabled, 30 second refresh rate

“Set Teredo Server Name” set: Enabled, Server name: “win1807.ipv6.microsoft.com”

“Set Teredo State” set: Enabled, State: Client or Enterprise (try both)
```

My fix was inspired by OG-Lomeri’s post from two years ago https://www.reddit.com/r/Windows10/comments/9lh28u/how_to_fix_teredo_is_unable_to_qualify_issue_in/; however, his server name configuration didn’t work for me. I think it’s been updated? The server name I used is from https://support.xbox.com/en-US/help/hardware-network/connect-network/troubleshoot-party-chat

Hope this works for you all.