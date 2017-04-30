Papertrail: log management right from your browser

Papertrail is a neat tool that let you access and handle your system logs right from the browser (provided you don't mind sending your logs to a third-party operator).

Aside from the many features provided by the application for the task (via rsyslog/syslog-ng facilities), it also let you add logs from other applications or tools as well.

Let's say I want to reach my `fail2ban` log too, I can easily send it over a secure TLS connection using the provided [remote\_syslog2](http://help.papertrailapp.com/kb/configuration/configuring-centralized-logging-from-text-log-files-in-unix/#remote_syslog) script like this:

<a href="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/papertrail_ds.jpeg">
   img src="https://raw.githubusercontent.com/i90rr/i90rr.github.io/master/resources/img/papertrail_ds.jpeg style="width: 400px; height: 43px;">
</a>

Tags: logs
