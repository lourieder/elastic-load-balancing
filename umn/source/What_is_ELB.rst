============
What Is ELB?
============

Elastic Load Balancing (ELB) automatically distributes incoming traffic across multiple backend servers based on the listening rules you configure. 
ELB expands the service capabilities of your applications and improves their availability by eliminating single points of failure (SPOFs).


|ELB Components|


ELB Components
==============

ELB consists of the following components:

    Load balancer: distributes incoming traffic across backend servers in one or more availability zones (AZs).
    Listener: uses the protocol and port you specify to check for requests from clients and route the requests to associated backend servers based on the listening rules you define. 
    You can add one or more listeners to a load balancer.
    Backend server group: routes requests from the load balancer to one or more backend servers. 
    You need to add at least one backend server to a backend server group.

    You can set a weight for each backend server based on their performance.

    You can also configure health checks for a backend server group to check the health of each backend server. 
    When a backend server is unhealthy, the load balancer stops routing new requests to this server.

Figure 1 ELB components

|ELB_FigOne.png|

Load Balancer Type

ELB provides the following types of load balancers: dedicated load balancer, shared load balancer, and classic load balancer. 
Dedicated load balancer and shared load balancer are called elastic load balancers collectively.
Dedicated load balancers have exclusive use of underlying resources, so that the performance of a dedicated load balancer is not affected by other load balancers.
 In addition, there are a wide range of specifications available for selection.

|note.png|

- In the eu-de region, you can create both dedicated and shared load balancers, and you can create either type of load balancers on the management console or by calling APIs. 
- In the eu-nl region, you can only create dedicated load balancers, either on the console or by calling APIs.

    Shared load balancers are deployed in clusters and share underlying resources, so that the performance of a load balancer is affected by other load balancers. Shared load balancers were previously named enhanced load balancers.
    Classic load balancers can handle simple, light-traffic web services.

|note.png|

    Classic load balancers can no longer be created on the management console. Use shared load balancers or dedicated load balancers instead.


For details, see :ref:`Differences Between Dedicated and Shared Load Balancers<umn/spurce/Differences_DedicatedandSharedLB>

For details, see :ref:`Differences Between Shared and Classic Load Balancers<umn/source/Differences_SharedandClassicLB>

Accessing ELB
=============

You can use either of the following methods to access ELB:

- Management console

    Log in to the management console and choose Network > Elastic Load Balancing (ELB).

-APIs

    You can call APIs to access ELB. For details, see the Elastic Load Balancing API Reference.

    In the eu-de region, you can create both dedicated and shared load balancers, and you can create either type of load balancers on the management console or by calling APIs.

    In the eu-nl region, you can only create dedicated load balancers, either on the console or by calling APIs.

.. |ELB Contents| image:: /source/media/ELB_Components.png 
.. |ELB_FigOne.png| image:: api-ref/source/media/ELB_FigOne.png
.. |note.png| image:: api-ref/source/media/note.png
