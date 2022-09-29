To start collecting Linux system logs enable logging then:
	sudo usermod -a -G systemd-journal dd-agent

Also needed to add a conf.yaml in the /etc/datadog-agent/conf.d/journal.d folder.

This only seems to be for Ubuntu as this is not a folder on a CentOS system.
logs:
    - type: journald
      path: /var/log/journal/  #Ubuntu
      path: /run/log/journal/

The journalctl command works on CentOS, so need to figure out how to do logging.
