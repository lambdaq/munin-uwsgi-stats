munin-uwsgi-stats
=================

Detailed uwsgi stats plugin for munin. In order to get the stats it
uses both the uwsgi `stats server`_ and the operating system's process
list (for stuff that's not available through the stats server, or
wherever the stats server sucks).

 I don't look uwsgi_rss/psutil/uwsgi's master... and tcp socket just uds/af_unix/file socket

Installation
------------
::

    pip install psutil
    wget -O /usr/share/munin/plugins/uwsgi_  https://github.com/el-dge/munin-uwsgi-stats/raw/master/uwsgi_
    chmod 755 /usr/share/munin/plugins/uwsgi_
    ln -s /usr/share/munin/plugins/uwsgi_ uwsgi_avg_rt
    ln -s /usr/share/munin/plugins/uwsgi_ uwsgi_exceptions
    ln -s /usr/share/munin/plugins/uwsgi_ uwsgi_listen_queue
    ln -s /usr/share/munin/plugins/uwsgi_ uwsgi_listen_queue_errors
    ln -s /usr/share/munin/plugins/uwsgi_ uwsgi_requests
    ln -s /usr/share/munin/plugins/uwsgi_ uwsgi_tx


Configuration
-------------

1. add the `stats server`_ to your uWSGI config and restart uWSGI (for
   example, use 127.0.0.1:4999; try "nc 127.0.0.1 4999" to see if
   there's any JSON output).

   .. _stats server: https://uwsgi-docs.readthedocs.io/en/latest/StatsServer.html

2. edit `/etc/munin/plugin-conf.d/munin-node`::

     [uwsgi_*]    
     user root
     env.port 4999
     env.name My_uwsgi

   The port can be either a TCP port or the filename to a unix domain
   socket. The uwsgi server must run on localhost; if the specified
   port is a TCP port, the host is assumed to be 127.0.0.1.

   If you are monitoring more than one uwsgi applications you can
   specify many ports and names, like this::

      [uwsgi_*]
      user root
      env.port 4999 4998 4997
      env.name app1 app2 app3

3. If systemd and file StatsServer.sock into `/home`: Modify ProtectHome to `read-only` in munin-mode.service

License
-------

Modified BSD - see file LICENSE for details
