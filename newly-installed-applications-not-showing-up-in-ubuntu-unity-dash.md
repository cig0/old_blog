Newly installed applications not showing up in Ubuntu 15.10 & 16.04 LTS Unity Dash 
[As of 2016-03-11](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1506744/comments/27)

<br>
<a href="http://www.ubuntu.com/download">
<img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/logo-ubuntu_-black_orange-hex.png" style="text-align: center; margin: auto;">
</a>

<br>
There's an annoying bug that prevents applications installed via a DEB file, be it either via CLI or the Ubuntu Software Center, from showing up in dash after being installed.

A bug report under the name of **Newly installed applications do not show in the dash** was initially filled on October 16th, 2015 (!) and despite this being a highly annoying usability breakage it has been classified since then as of 'low importance' (!!).

The bug report can be found here: [Bug #1506744](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1506744).

Anyhow, [comment #12](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1506744/comments/12) by _Dan Jared_ offers a workaround that works for me:
<blockquote>Kill the process /usr/bin/unity-scope-loader</blockquote>

<br>
Tags: ubuntu, unity