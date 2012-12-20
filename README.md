munin-uwsgi-stats
=================

Detailed uwsgi stats plugin for munin

Install:

    sudo wget -O /usr/share/munin/plugins/uwsgi_  https://github.com/stevetu/munin-uwsgi-stats/raw/master/uwsgi_
    sudo chmod 755 /usr/share/munin/plugins/uwsgi_
    sudo vi /usr/share/munin/plugins/uwsgi_ #edit UWSGI_STATS for host
    sudo /usr/share/munin/plugins/uwsgi_ install 

License: BSD

Related work:
 - http://projects.unbit.it/uwsgi/wiki/StatsServer
 - https://github.com/unbit/uwsgitop/blob/master/uwsgitop
 - https://github.com/jarus/munin-uwsgi
    this one only trackes memory & process

