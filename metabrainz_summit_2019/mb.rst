:title: MetaBrainz Summit 2019 - Resources
:data-transition-duration: 800
:css: mb.css
:skip-help: true

This is a presentation of system resources, their usage, etc for MetaBrainz Summit 2019

You can render this presentation to HTML with the command::

    hovercraft mb.rst

And connect with a browser to http://localhost:8000

.. header::

    .. image:: images/background.png

 
 .. footer::

    "System & Network Resources", Laurent Monin, MetaBrainz Summit 2019 

----

:hovercraft-path: M 40000,60000 a 40000 40000 0 0 0 80000,0 a 40000 40000 0 0 0 -80000,0 Z


MetaBrainz Summit 2019
======================

Our infrastructure
------------------


----

Number of servers
=================

* Hetzner: 20 physical machines (=2018)

* Hetzner Cloud: 15 virtual machines (8 in 2018)

* Google Cloud: 7 active instances (12 in 2018)

* Total: **42 servers**

.. note::

    TODO

----

Memory, storage, processing power
=================================

* 1.5 Terabytes of RAM

* 18 Terabytes of storage

* 1.7M Bogomips on 240 CPU cores


.. note::

    TODO.

----


Network traffic
===============

* *180 Terabytes* served this year

* *~50 mbits/s* out, *20 mbits/s* in

* *120* mbits/s out before, due to QNAP


----

Latency
=======


.. image:: images/ping_latency_world.png
    :height: 600px

.. note::
    Ping to kiki.mb.o from different parts of the World

----

:id: mbs1

MusicBrainz Services I
======================

Number of queries served this year
  
**11 Billions** of 200s answers


----


MusicBrainz Services II
=======================

* Incoming Requests: *850 req/s*

* Handled by upstreams: **280 req/s**

----


MusicBrainz Services III
========================

* MB Website mean response time: **240 ms**
* WS mean response time a bit worse: 20 to 30ms



----

SOLR
====

* 6 servers on Hetzner Cloud
* *180 req/s* during peak time
* Worst mean response time: *125 ms*
* Best mean response time: 75 ms
* full redundancy, automatic fail over

----

Hetzner Cloud I
===============

* Hosting adds 10ms latency on WS (more hops)
* VM CPU performance isn't guaranteed

----

Hetzner Cloud II
================

* low cost: 99€ / month for 6 VMs (SOLR)
* convenient
* not 100% on, due to Hetzner maintenance ops

----

Docker I
========

* *170* containers running
* our setup is not standard enough
* kubernetes is still very far

----

Docker II
=========

* some issues related to git2consul
* docker-server-configs critical

----

Docker III
==========

* volumes management is a pain
* some containers are critical
* restarting docker / rebooting machine not possible



----

Stability
=================

* 99.9% availability of core services
* limited failure impact
* crappy cpu fans (6 were replaced)
* still too many **SPoFs**

----

Soon...
=======

* work at reducing SPoFs
* improved database backups using Barman
* moving more services to VMs
* upgrading to 18.04
* upgrading docker + consul


----


Thanks !
========

Made with Hovercraft_ and Critical

.. _Hovercraft: https://github.com/regebro/hovercraft
