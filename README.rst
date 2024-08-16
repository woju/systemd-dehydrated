Dehydrated integration with systemd, with ACME Renewal Information (ARI) checker
================================================================================

This is my take on integrating dehydrated with nginx and running it off
systemd's timers. Also has ARI checker.

Installation
------------

::

    sudo apt-get build-dep ./
    debuild
    sudo apt-get install ../systemd-dehydrated*.deb

Configuration
-------------

::

    sudo cp contrib/nginx-default.conf /etc/nginx/sites-enabled/default
    sudo systemctl reload nginx
    sudo systemctl enable --now dehydrated@domain.example.timer
    # only the first time, when you need to renew the cert immediately:
    sudo systemctl start dehydrated@domain.example.service

You can also have multiple domains per cert::

    sudo systemctl enable --now dehydrated@domain1.example\\x20domain2.example.timer

NOTE you don't configure domains.txt, it's ignored by this undertaking

.. vim: tw=80
