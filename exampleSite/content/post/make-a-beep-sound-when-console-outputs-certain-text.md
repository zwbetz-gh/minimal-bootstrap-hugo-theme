---
title: "Make a beep sound when console outputs certain text"
date: 2018-09-18T21:07:39-05:00
publishdate: 2018-09-18
lastmod: 2018-09-18
draft: false
---

Originally this was a question posed on the [hugo discussion forums](https://discourse.gohugo.io/t/can-hugo-server-notify-with-audio-on-error/14247). 

When running `hugo server`, the user wanted to be notified with a beep of any error messages that were output by the console. 

This isn't a use case for me personally but I thought it was a fun problem to solve. 

---

My original solution for Mac:

```bash
hugo server 2>&1 | tee /dev/tty | while read line ; do echo $line | say --rate=500 ; done
```

Explained: 

`hugo server 2>&1` -- Redirect `stderr` to `stdout`, then pipe `stdout`

`tee /dev/tty` -- Pipe `stdout` while still showing it in the console

`while read line ; do echo $line` -- Echo each line, then pipe it

`say --rate=500` -- Use the Mac `say` command to read from `stdin` at a rate of 500 words per minute

---

The user then mentioned he was on Windows, so I tweaked it and gave him additional instructions:

1. Download and install [git bash](https://git-scm.com/downloads)
2. Download [voice.exe](https://www.elifulkerson.com/projects/commandline-text-to-speech.php) then add it to your `PATH`
3. In a git bash window run: 

```bash
hugo server 2>&1 | tee /dev/tty | while read line ; do echo $line | if [[ $line = *"ERROR"* ]] ; then voice.exe --rate=10 ; fi ; done
```

Explained: 

`if [[ $line = *"ERROR"* ]] ; then voice.exe --rate=10 ; fi` -- This time, only speak the line if it contains the text `ERROR`. And since it's Windows, use `voice.exe` at its fasted rate of speech, `10`

---

Finally, after more research, I came up with this solution to address the original question:

```bash
hugo server 2>&1 | tee /dev/tty | while read line ; do echo $line | if [[ $line = *"ERROR"* ]] ; then rundll32 user32.dll,MessageBeep ; fi ; done
```

Explained: 

`rundll32 user32.dll,MessageBeep` -- Instead of speaking the line, actually make a "beep" sound by using the [Windows MessageBeep function](https://docs.microsoft.com/en-us/windows/desktop/api/winuser/nf-winuser-messagebeep)

See [Windows Rundll and Rundll32 interface](https://support.microsoft.com/en-us/help/164787/info-windows-rundll-and-rundll32-interface) for more info. 
