---
title: "Mac (and Linux) to Windows command line mappings"
date: 2018-09-21T22:31:25-05:00
publishdate: 2018-09-22
lastmod: 2018-09-25
draft: false
---

<table class="table table-bordered">
    <thead class="thead-light">
        <tr>
            <th scope="col">Description</th>
            <th scope="col">Mac/Linux</th>
            <th scope="col">Windows</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td scope="row">Display all contents of a dir</td>
            <td><code>ls -al</code></td>
            <td><code>dir</code></td>
        </tr>
        <tr>
            <td scope="row">Change dir</td>
            <td><code>cd DIR</code></td>
            <td><code>cd DIR</code></td>
        </tr>
        <tr>
            <td scope="row">Rename file</td>
            <td><code>mv FILE FILE</code></td>
            <td><code>ren FILE FILE</code></td>
        </tr>
        <tr>
            <td scope="row">Copy file</td>
            <td><code>cp SRC DEST</code></td>
            <td><code>copy SRC DEST</code></td>
        </tr>
        <tr>
            <td scope="row">Delete file</td>
            <td><code>rm FILE</code></td>
            <td><code>del FILE</code></td>
        </tr>
        <tr>
            <td scope="row">Delete dir</td>
            <td><code>rm -rf DIR</code></td>
            <td><code>rmdir /s/q DIR</code></td>
        </tr>
        <tr>
            <td scope="row">Display file to stdout</td>
            <td><code>cat FILE</code></td>
            <td><code>type FILE</code></td>
        </tr>
        <tr>
            <td scope="row">Print current working dir</td>
            <td><code>pwd</code></td>
            <td><code>cd</code></td>
        </tr>
        <tr>
            <td scope="row">Change file timestamp</td>
            <td><code>touch FILE</code></td>
            <td><code>type nul > FILE</code></td>
        </tr>
        <tr>
            <td scope="row">Display current user</td>
            <td><code>whoami</code></td>
            <td><code>echo %USERNAME%</code></td>
        </tr>
        <tr>
            <td scope="row">Display all env vars</td>
            <td><code>env</code></td>
            <td><code>set</code></td>
        </tr>
        <tr>
            <td scope="row">Print PATH</td>
            <td><code>echo $PATH</code></td>
            <td><code>echo %PATH%</code></td>
        </tr>
        <tr>
            <td scope="row">Show full path of a command</td>
            <td><code>which COMMAND</code></td>
            <td><code>where COMMAND</code></td>
        </tr>
        <tr>
            <td scope="row">Search file for pattern, ignore case</td>
            <td><code>grep -i "PATTERN" FILE</code></td>
            <td><code>findstr /i "PATTERN" FILE</code></td>
        </tr>
        <tr>
            <td scope="row">Search for file recursively</td>
            <td><code>find . -name FILE</code></td>
            <td><code>dir FILE /b/s</code></td>
        </tr>
        <tr>
            <td scope="row">Display networking info</td>
            <td><code>ifconfig</code></td>
            <td><code>ipconfig /all</code></td>
        </tr>
        <tr>
            <td scope="row">Display aliases</td>
            <td><code>alias</code></td>
            <td><code>doskey /macros</code></td>
        </tr>
        <tr>
            <td scope="row">Create alias</td>
            <td><code>alias ALIAS="COMMAND"</code></td>
            <td><code>doskey ALIAS=COMMAND</code></td>
        </tr>
    </tbody>
</table>
