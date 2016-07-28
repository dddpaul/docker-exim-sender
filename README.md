Based on https://github.com/miracle2k/dockerfiles/tree/master/exim-sender.

Exim 4 specifically configured to act as an outgoing SMTP service. Bounces
go a local directory in ``/var/spool/exim4/bounces``.


Environment variables:
----------------------

``ALLOWED_HOSTS``
  ``;`` separated list of allowed senders. Used within an Exim hostlist,
  may include networks (``192.168.23.0/24 : my.friend.example``).

``PRIMARY_HOST``
  Exim's ``primary_hostname`` setting; you should also be able to specify
  a hostname for your Docker container instead.

``SMTP_PORTS``
 Exim's ``daemon_smtp_ports`` setting, "25 : 587" by default.


Example:
--------

    docker run --net=host -v /tmp/exim:/var/spool/exim4 -e PRIMARY_HOST=example.org -e ALLOWED_HOSTS="194.168.59.1/16" -e SMTP_PORTS=10025 dddpaul/exim-sender


Volumes you may want to share:
------------------------------

/var/spool/exim4


TODO:
-----

  - Support TLS
  - Support authentication as alternative to ip-based lockdown
