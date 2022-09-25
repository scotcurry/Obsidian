To start collecting Linus system logs enable logging then:
	sudo usermod -a -G systemd-journal dd-agent

Also needed to add a conf.yaml in the /etc/datadog-agent/conf.d/journal.d folder.

logs:
    - type: journald
      path: /var/log/journal/
