=====================
Application Scenarios
=====================

Heavy-Traffic Applications
==========================

For an application with heavy traffic, such as a large portal or mobile app store, 
ELB evenly distributes incoming traffic to multiple backend servers, 
balancing the load while ensuring steady performance.

Sticky sessions ensure that requests from one client are always forwarded to the same backend server for fast processing.
*Figure 1* Session stickiness

|ApplicationScernariosFig_01.png|

Applications with Predictable Peaks and Troughs in Traffic
==========================================================

For an application that has predictable peaks and troughs in traffic volumes,
ELB works with AS to add or remove backend servers to keep up with changing demands.
An example is flash sales, during which application traffic spikes in a short period.
ELB can work with AS to run only the required number of backend servers to handle the load of your application.
*Figure 2* Flexible scalability

|ApplicationScernariosFig_02.png|

Zero SPOFs
==========

ELB routinely performs health checks on backend servers to monitor their healthy state.
If any backend server is detected unhealthy, ELB will not route requests to this server until it recovers.

This makes ELB a good choice for running services that require high reliability, such as websites and toll collection systems.
*Figure 3* Eliminating SPOFs

|ApplicationScernariosFig_03.png|

Cross-AZ Load Balancing
=======================

ELB can distribute traffic across AZs. When an AZ becomes faulty, ELB distributes traffic across backend servers in other AZs.

ELB is ideal for banking, policing, and large application systems that require high availability.
*Figure 4* Traffic distribution to servers in one or more AZs

|ApplicationScernariosFig_04.png|


.. |ApplicationScernariosFig_01.png| image:: api-ref/source/media/ApplicationScernariosFig_01.png
.. |ApplicationScernariosFig_02.png| image:: api-ref/source/media/ApplicationScernariosFig_02.png
.. |ApplicationScernariosFig_03.png| image:: api-ref/source/media/ApplicationScernariosFig_03.png
.. |ApplicationScernariosFig_04.png| image:: api-ref/source/media/ApplicationScernariosFig_04.png
