=======================================================
Differences Between Dedicated and Shared Load Balancers
=======================================================

Each type of load balancer has their advantages.


- In the eu-de region, you can create both dedicated and shared load balancers,
    and you can create either type of load balancers on the management console or by calling APIs.
- In the eu-nl region, you can only create dedicated load balancers, either on the console or by calling APIs.

Feature Comparison
==================

Dedicated load balancers provide more powerful forwarding performance, while shared load balancers are less expensive. 
You can select the appropriate load balancer based on your application needs. 
The following tables compare the features supported by the two types of load balancers.
(√ indicates that an item is supported, and x indicates that an item is not supported.)
*Table 1* Performance


+------------+----------------------------+-----------------------------------------------------------------------------------+
| Item       | Dedicated Load Balancers 2 | Shared Load Balancers                                                             |
+============+============================+===================================================================================+
|Deployment mode|Each dedicated           |  Shared load balancers are deplayment in                                          |
+------------+----------------------------| Clusters, and all load balnacers share underlying resources,                      |
| body row 2 |                            | so that the performance of a load balancer i saffected by other load balancers    |             
+------------+----------------------------+-----------------------------------------------------------------------------------+
| body row 3 | Cells may                  | - Cells                                                                           |
+------------+----------------------------+-----------------------------------------------------------------------------------+
| body row 4 |                            | - blocks.                                                                         |                                                                                                 
+------------+----------------------------+-----------------------------------------------------------------------------------+