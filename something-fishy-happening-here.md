Fish shell: finally, a command line shell for the 90's

<p style="text-align: center; font-size: small;">This is an old post I'm reproducing here as part of my old blog migration. Since I wrote this post<br>I changed my habits quite a bit but the article is still valid as last time I checked using Fish as the default shell<br>in my Fedora 23 system I couldn't log into the X session</p>

<p style="font-size: x-large; text-align: center;">Why you shouldn't set <a href="https://www.fishshell.com">Fish</a> as the default shell
<br><span style="font-size: large;">Tip: it's ok though to set it as your <b>primary</b> shell</span>
</p>

When I decided barely a month ago to finally move from Bash to Zsh I did remember about Fish, a shell I had tried in the past but ultimately left to test later as I didn't had the time at that opportunity to dive into it the way I pretended.

When I finally got a whole weekend for a n3rd sprint I deeply, desperately, passionately and unconditionally fell in love with Fish.

Right straight after reading Fish's website I could sense this would be the beginning of something special, as reading about it's design argument I felt the same way as when I read about [The Arch Way]() some years ago and fell in love with the distro.

I believe the best way I can present this Friendly Interactive Shell is by describing it as __an intelligent shell that works as an extension of the user in an organic and natural way__:

<div class="center">
    <img class="center" src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/11-fish-shell1.png" align="center"/>
    <span>Screenshot taken from: http://lwn.net/images/2013/11-fish-shell.png</span>
</div>
<br>

----

<br>
But as stated on its wiki Fish design isn't 100% POSIX compliant (and this will put a lot of people down, for sure) so there's a chance that you will break your system if you set it as the default shell, depending on your configuration, specially as some sensible system scripts like /etc/profile usually doesn't explicitly declare which shell should run them as they lack the required shebang on its header (I say this is a bug, not a feature). Take for instance a fresh Ubuntu 14.04 LTS install: you wont be able to log to your Unity session if you:<code> # chsh /usr/bin/fish</code>.

An interesting option would be launching Fish as a login shell, in tmux you can do:

<code>
~ > cat .tmux.conf
<br>\# Let's grab some fresh Fish
<br>set-option -g default-shell "/usr/bin/fish"
<br>...
</code>

Now to launch tmux + Fish as a login shell you can stick this simple snippet borrowed from Arch Linux's tmux wiki into your ~/.bash_profile (or ~/.profile depending on how your system is set up):

<code>
\# tmux
<br>if which tmux 2>&1 >/dev/null; then
<br>     \# if session is started then attach to it, if not start a new one
<br>     test -z ${TMUX} && (tmux -2 attach-session || tmux -2 new-session)
<br>fi
</code>

Note that the -2 flag is there to force tmux to assume the terminal supports 256 colors, YMMV.

Finally, a full ~/.bash_profile could look like this one:
<script lang="sh" src="https://gist.github.com/i90rr/70a892b45fdf488b949f.js"></script>

<br>
Now every time you create a new vty by launching an emulator, by SSH-ing to your system, by creating a new instance within tmux or by switching to a tty you will be greeted by tmux sporting an elegant and intelligent shell :)

What? You don't know why Fish is so special? Don't waste your time reading my crap but instead rush to its website at [www.fishshell.com](https://www.fishshell.com) and grab a copy - you can thank me later :)

Tags: fish, shell, terminal
