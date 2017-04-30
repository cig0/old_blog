Papertrail: log management right from your browser

[Papertrail](https://papertrailapp.com) is a neat tool that let you access and handle your system logs right from the browser (provided you don't mind sending your logs to a third-party operator).

Aside from the many features provided by the application for the task (via rsyslog/syslog-ng facilities), it also let you add logs from other applications or tools as well.

Let's say I want to reach my `fail2ban` log too, I can easily send it over a secure TLS connection using the provided [remote\_syslog2](http://help.papertrailapp.com/kb/configuration/configuring-centralized-logging-from-text-log-files-in-unix/#remote_syslog) script like this:
<br/><br/>

<div style="display: flex; justify-content: center;">
     <a href="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/papertrail_ds.jpeg">
     	<img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/papertrail_ds.jpeg" style="width: 700px; height: 75px;">
     </a> 
</div>
<span style="margin: 0px auto; display: flex; justify-content: center; text-align: center; vertical-align: top; font-size: small;">Click to enlarge</span>

Note: I forgot to edit the default configuration file to comment out or remove the nonexistent example file locallog.txt

Tags: logs
