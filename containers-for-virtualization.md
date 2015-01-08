
# Containers and virtualization

Problem: How do we meet peak usage demand?

Historically you did two things

1. Write more efficient software
2. Buy more hardware resources

This created anther problem.

Problem: How come I need to have a system that is 99% idle all the time, is their something cheaper?

Solution run more things on the hardware to drop the idle percentage but then you get cought back again when you need peak use resources...

This lead to hardware virtualization.  

Hardware Virtualization provided some benefits

1. OS level isolation
2. Process level isolation

This means you could create a virtual machine with its own set of users, applications and resources attached to it.  You could even mix and match hardware to requirements. E.g. You have a process that doesn't leverage multi-core/multi-CPU hardware - no problem just create a virtual machine with a single core and leave the rest available to other virtual machines.

Problem: We have all these virtual machines and their consuming all these resources but most of the time the resources are under used? (sound familiar?)

Solutions - Containers.

Back when VM (Virtual Machines) became popular their was another approach. Process and resource Isolation in via something called chroot and eventually reconceived as "containers".  This was pioneered as a comercial product by Sun Microsystem in their Zones and Containers.  When Sun died the idea didn't go away. The Linux community picked up some of the same ideas and created something called cgroups. The opperating system can present a clean slate of resources to a container as if it owned the whole machine. It can do this over and over with multiple containers until all resources are used up (in which case you migrate your containers to another VM or physical hardware device).  

The abstraction of the container is lighter weight then a virtual machine because it can re-use the host operating system with still achieving a large degree of resource isolation.  E.g. you need to run a system that calls for Apache 2, PHP 5.4 and other service that calls for Apache 2 but must have PHP 5.6. You could use the same machine but run them in separate containers without one interfering with another since each container believes it has the whole machine (I am simplifying here for brevity).

What does this mean for ITS or Web Services

Think about system upgrades. Operating system upgrades happen rarely but language and platform upgrades happen more frequently (e.g. WP updates every few weeks, we might want to roll out custom code more often).  If you have systems running behind a load balancer (so traffic is routed to available machines) you could bring down one container replacing it with a new one quickly (e.g. a few seconds as opposed to a few minutes to bring up a Virtual Machine).

Another important difference is that you can hand a contianer to a developer.  They can add to the container and then hand that to testing/QA and production. You don't wory about dependency mismatch (e.g. PHP/MySQL library versions) because they can be included in the container.  So you have WP and it now needs.

Today their are three container projects that have traction - Docker (with support pledged by all the major IAAS/PAAS), Rocket (a fork from Docker backed by Google/CoreOS) and Mesos (an apache project, is now supports Docker containers).

Container management is the big area of sorting out with Kubernetes from Google being the strong horse in the race.


Links:

+ [Co-Existence of Containers and Virtualization Technologies](http://redhatstackblog.redhat.com/2014/11/20/co-existence-of-containers-and-virtualization-technologies/)
+ [What is docker and why is it so darn popular](http://www.zdnet.com/article/what-is-docker-and-why-is-it-so-darn-popular/)
+ [Operating-system-level virtualization](http://en.wikipedia.org/wiki/Operating-system-level_virtualization)
+ [Hardware virtualization](http://en.wikipedia.org/wiki/Hardware_virtualization)
+ [Docker](https://www.docker.com/)
+ [Kubernetes](http://kubernetes.io/news/)

