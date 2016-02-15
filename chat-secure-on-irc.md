Chat safely (and privately!) on Freenode IRC with WeeChat

<h4>Head-to-toe guide for registering an account + SASL + cloaking + SSL + OTR</h4>

<img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/weechat.png" border="0"  align="left" style="margin-right: 17px">
This is a hand-holding step-by-step guide to use the Freenode IRC network to chat safely out of the reach of prying eyes; the goal is to save you time when setting up such setup.
<br><br>
**Introduction**

If you're reading this post it's (most likely) because you're concerned about [your] privacy online, you are an IRC user and most probably you make your systems work the way _you_ want.
<br>Conversely if you are concerned about privacy online but you don't know how to apply this guide just leave me a comment and I will try to help you find the best solution that suits your needs.
While this guide is focused on Freenode and WeeChat it should be trivial to adapt it to other networks and clients.

**Hands-on!**

1. First, [register a new Freenode account](https://freenode.net/faq.shtml#nicksetup)
2. Proceed to [configure WeeChat to log via SASL](https://www.weechat.org/files/doc/stable/weechat_user.en.html#irc_sasl_authentication) (SASL on [Wikipedia](https://en.wikipedia.org/wiki/Simple_Authentication_and_Security_Layer), [Freenode]( https://freenode.net/sasl/))
<br>This is a convenient method to authenticate yourself and indeed a better one than using a password most of the times because:
    <ul>
    <li>You don't need to type your password every time you log in to the network</li>
    <li>In case you configure your client to automatically log in be aware that some clients still store credentials in plain text, which is a potential security risk</li>
    <li>Sometimes depending on the quality of your connection authenticating by a password may fail, with SASL it will not</li>
    <li>SASL will prevent most if not all attempts from stealing your nick. I remember when I still used to authenticate via a password that from time to time I had to fight with script kiddies and alike, issuing /GHOST and /RELEASE commands to NickServ in order to regain control of my nick. Authenticating with SASL that's now part of the past!</li>
    <li>Depending on the load of the server you connect to and the way your client works [it may be a delay until the cloak is applied](https://freenode.net/faq.shtml#nocloakonjoin) when aythenticating via password method, this is why sometimes you see that a user enters a channel with his/her public IP address to moments later switch to the cloaked mode.
    </ul>
3. Welcome to Freenode! You can start working on your privacy now. Your first step should be to head to #freenode and [ask the friendly staff there for a cloak](https://freenode.net/faq.shtml#cloaks)
4. Next stop will be to [enforce the use of an SSL layer](https://weechat.org/files/doc/weechat_faq.en.html#irc_ssl_freenode) to secure (encrypt) the communication between your WeeChat client and the server
5. Fifth step: [implement the Off-the-Record protocol](https://github.com/mmb/weechat-otr) and enjoy

I don't foresee you have any issues following these steps - I myself did configure OTR a few days ago this way - but should you happen to find a blocker just leave a comment below.


Tags: irc, weechat, privacy, security, ssl, sasl, otr, comms
