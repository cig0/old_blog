Person-to-person private communications on freenode IRC with WeeChat

<h4>Head-to-toe guide for registering an account + SASL + cloaking + SSL + OTR</h4>

<img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/weechat.png" border="0"  align="left" style="margin-right: 17px">
This guide shows you how to implement a private _person-to-person_ communication channel in freenode <br>to safely avoid server logging of your chats.
<br><br>

**Introduction**

There are plenty of ways to securely chat online, however if you spend most of your time in freenode and indeed the people you chat with is there this method will help you establish a secure, private channel for a person-to-person communication. 

While this guide is focused on freenode and WeeChat it should be trivial to adapt it to other networks and clients.
<br><br>

----

<br>
**Hands-on!**

1. Start by [registering a new freenode account](https://freenode.net/faq.shtml#nicksetup)
2. Proceed to [configure WeeChat to log via SASL](https://www.weechat.org/files/doc/stable/weechat_user.en.html#irc_sasl_authentication) (SASL on [Wikipedia](https://en.wikipedia.org/wiki/Simple_Authentication_and_Security_Layer), [freenode]( https://freenode.net/sasl/))
<br>This is a convenient method to authenticate yourself and indeed a better one than using a password most of the times because:
    <ul>
    <li>You don't need to type your password every time you log in to the network</li>
    <li>In case you configure your client to automatically log in be aware that some clients still store credentials in plain text, which is a potential security risk</li>
    <li>Sometimes depending on the quality of your connection authenticating by a password may fail, with SASL it will not</li>
    <li>Depending on the load of the server you connect to and the way your client works [it may be a delay until the cloak is applied](https://freenode.net/faq.shtml#nocloakonjoin) when aythenticating via password method, this is why sometimes you see that a user enters a channel with his/her public IP address to moments later switch to the cloaked mode
    </ul>
3. Welcome to freenode! You can start working on your privacy now. Your first step should be to head to #freenode and [ask for a cloak](https://freenode.net/faq.shtml#cloaks). A cloak hides your connection details from the rest of the freenode users but it doesn't work with web IRC clients
4. Next stop will be to [enforce the use of an TLS SSL layer](https://weechat.org/files/doc/weechat_faq.en.html#irc_ssl_freenode) to secure (encrypt) the communication between your WeeChat client and the server
5. Fifth step: [implement the Off-the-Record protocol](https://github.com/mmb/weechat-otr)

I don't foresee you have any issues following these steps - I myself did configure OTR this way a few days ago - but should you happen to find a blocker just leave a comment below.

**Final note**

Do remember that privacy and security oriented technologies - as much as almost every other these days - are continuouslly evolving so what may be the best option for today may be doesn't for tomorrow.

I recommend you to check this neat directory of privacy-oriented applications and services: [Prism Break](https://prism-break.org/en/all)

Last but no least I want to thank the guys at #freenode that helped me correct some inaccurate stuff and misbelieves about how some of the freenode stuff works.

Tags: irc, weechat, privacy, security, ssl, sasl, otr, comms
