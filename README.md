munin-uwsgi-stats
=================

Detailed uwsgi stats plugin for munin

Install:
--------------------

    sudo wget -O /usr/share/munin/plugins/uwsgi_  https://github.com/stevetu/munin-uwsgi-stats/raw/master/uwsgi_
    sudo chmod 755 /usr/share/munin/plugins/uwsgi_
    sudo vi /usr/share/munin/plugins/uwsgi_ #edit UWSGI_STATS for host
    sudo /usr/share/munin/plugins/uwsgi_ install 

Config & test:
--------------------

1. add stats server (see [1]) to your uWSGI config, restart uWSGI, e.g. use 127.0.0.1:4999
2. use `nc 127.0.0.1 4999` to see if there's any JSON output
3. edit `/etc/munin/plugin-conf.d/munin-node`

    `[uwsgi_*]`    
    `env.addr 127.0.0.1:4999`

4. Alternatively, you can edit `uwsgi_` source code directly for the stats server address. The global variable is called `UWSGI_STATS`
5. `sudo munin-run uwsgi_requests` to test run munin

License:
--------------------

BSD

Related work:
--------------------
 - [1]: http://projects.unbit.it/uwsgi/wiki/StatsServer
 - [2]: https://github.com/unbit/uwsgitop/blob/master/uwsgitop
 - [3]: https://github.com/jarus/munin-uwsgi   
        this one only trackes memory & process

