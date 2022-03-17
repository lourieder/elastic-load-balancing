=========================================
Using Shared Load Balancers — Entry Level
=========================================

Scenarios
=========

You have a web application, which often needs to handle heavy traffic and is deployed on two ECSs for load balancing.

You can create a shared load balancer to distribute traffic evenly across the two ECSs,
which eliminates SPOFs and makes your application more available.

Prerequisites
=============

    You have added security group rules to allow traffic from the ports used by the two ECSs. (Alternatively, you can enable all ports first and then disable the ports that are no longer used.)
    The security group containing the two ECSs allows traffic from 100.125.0.0/16. (ELB uses these IP addresses to perform health checks and route requests to backend servers.)

Creating ECSs
=============                                                                                                   

ECSs are used as backend servers.

Each ECS needs an EIP for accessing the Internet, so that The EIP bound to the ECS is required only for configuring ECS backend services in this example. You need to determine whether to bind an EIP to the ECS based on the service plan.

Determine whether you need to bind an EIP to your load balancer by referring to Load Balancing on a Public or Private Network.

    Log in to the management console.
    In the upper left corner of the page, click and select the desired region and project.
    Hover on in the upper left corner to display Service List and choose Computing > Elastic Cloud Server.

    Click Create ECS, configure the parameters, and click Create Now.

    The following table lists the specifications of the two ECSs.
