:title: MetaBrainz Summit 2022 - Resources
:data-transition-duration: 800
:css: mb.css
:skip-help: true

This is a presentation of system resources, their usage, etc for MetaBrainz Summit 2022

You can render this presentation to HTML with the command::

    hovercraft mb.rst

And connect with a browser to http://localhost:8000

.. header::

    .. image:: images/background.png

 
 .. footer::

    "System & Network Resources", Laurent Monin, MetaBrainz Summit 2022 

----

:hovercraft-path: M 40000,60000 a 40000 40000 0 0 0 80000,0 a 40000 40000 0 0 0 -80000,0 Z


MetaBrainz Summit 2022
======================

Current state of our infrastructure
-----------------------------------


----

Number of servers
=================

* Hetzner: 27 physical machines (20 in 2019)

* Hetzner Cloud: 12 virtual machines (15 in 2019)

* Google Cloud: 8 active instances (7 in 2019)

* Total: **47 servers**

.. note::

    TODO

----


Network traffic
===============

* *150 Terabytes* served this year (30 Tb less than in 2019)
* *~45 mbits/s* out, *35 mbits/s* in (50/25 back to 2019)
* Almost all our servers are in EU (Germany, Finland)
* reduction of traffic is mostly due to better filtering

----

Latency
=======


* Europe: < 40ms
* North America: ~100ms
* Asia / Africa: ~200-300ms (but ~50ms from Egypt)
* Australia / Oceania: ~300-400ms

.. note::
    Ping to kiki.mb.o from different parts of the World

----

:id: mbs1

MusicBrainz Services I
======================

Number of queries served this year
  
**10 Billions** of 200s answers (1B less than in 2019)


----


MusicBrainz Services II
=======================

* Incoming Requests: *650 req/s* (it was 850 in 2019)
* Handled by upstreams: **290 req/s** (280 in 2019)

----


MusicBrainz Services III
========================

* MB Website mean response time: **240 ms** (on par with 2019)
* WS mean response time: **130ms** (it degraded, it was ~40ms in 2019)



----

SOLR
====

* 7 servers, 2 load balancers + 5 backends
* *180 req/s* during peak time
* Worst mean response time: *290 ms* (125ms in 2019)
* Best mean response time: 55 ms (75ms in 2019)
* full redundancy, automatic fail over

----

Hetzner Cloud I
===============

* Hetzner vSwitch works well to connect VMs and dedicated servers
* intensive processing is to be avoided
* very fine for memory/network hungry apps
* VM CPU performance isn't guaranteed

----

Hetzner Cloud II
================

* *low cost*: 99€ / month for 6 VMs (SOLR)
* *convenient*
* not 100% on, due to Hetzner maintenance ops

----

Docker I
========

* *200+ containers* running
* docker-server-configs is almost driving everything

----

Docker II
=========

* git2consul was replaced by *gitzconsul* (Python-based, stick to our needs)
* *serviceregistrator* replaced registrator (now unmaintained)
* *consul* still has to be upgraded
* *consul-template* (Go template language sucks but it works)

----

Docker III
==========

* volumes management isn't easy, but we're documenting 
* old story, some containers are still critical (SPoFs)
* restarting docker is now possible without stoping containers, it helps for upgrades.

----

Stability
=========

* *99.9% availability* of core services
* limited failure impact
* it seems the crappy cpu fans series is over

----

Improvements I
==============

* *ansible* is now used to manage a good part of servers
* we ponder moving startup scripts to ansible, using it as deployment tool somehow
* we upgraded a bunch of servers to *20.04* (finally), but the process isn't over yet

----

Improvements II
===============

* *IPv6 support* is on the map
* new gateways will run soon, giving us more space to grow
* consul upgrade will come soon after we finished the move to ansible

----

Metrics
=======

* Prometheus + grafana + node_exporter (needs more work)
* Influxdb + grafana (legacy)
* Grafana new alert system is great, but also much more complex

Thanks !
========

* Special thanks to *atj*, whose help is welcome.
* Thanks to the amazing *MetaBrainz team*, who contribute to keep all our stuff on.
* Thanks to all users, who are keeping our crazy projects alive.


Made with Hovercraft_ and Critical

.. _Hovercraft: https://github.com/regebro/hovercraft
