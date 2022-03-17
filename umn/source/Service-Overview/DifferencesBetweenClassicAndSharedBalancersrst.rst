=====================================================
Differences Between Classic and Shared Load Balancers
=====================================================

Each type of load balancer has their advantages.

    - Classic load balancers are suitable for web services with low traffic and simple traffic patterns.
api-ref
    Classic load balancers can no longer be created on the management console. 
    
    Use shared load balancers or dedicated load balancers instead.
    Shared load balancers are suitable for choices for web services with heavy traffic. 
    (Shared load balancers were previously named enhanced load balancers.)

Table 1 compares the features supported by the two types of load balancers. √ indicates that an item is supported, and
 — indicates that an item is not supported.

+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
| Feature                  | Description                                                       | Classic load balanceer | Shared load balancer |     |     |     |
+==========================+===================================================================+========================+======================+=====+=====+=====+
|| Load balancing over     || - Each load balancer on a pblic network has a public IP          ||                       ||                     ||    ||    ||    |
|| public and private      || address bound to it and routes requests from clients to          || √                    || √                  ||    ||    ||    |
|| networks                || backend servers over the Internet.                               ||                       ||                     ||    |     |     |
||                         || - Load balancers on a private network work within a VPC and      ||                       ||                     ||    |     |     |
||                         || route requests from clients to backend servers in the same       ||                       ||                     ||    |     |     |
||                         || VPC.                                                             ||                       ||                     ||    |     |     |
||                         ||                                                                  ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Layer 4 and Layer 7     || - Layer 4 load balancing: After rechieving TCp and UDP requests  ||                       ||                     ||    |     |     |
|| load balancing          || from the clients, the load balancer directly routes the requests || √ (UDP is not        || √                  ||    |     |     |
||                         || to backend servers. Load balancing at Layer 4 features high      || supported for load    ||                     ||    |     |     |
||                         || routing efficiency.                                              || balancers on a        ||                     ||    |     |     |
||                         || - Layer 7 load balancing: After rechieving an HTTPS or HTTPS     || private network.)     ||                     ||    |     |     |
||                         || request, the laod balancer identifies the fields in the          ||                       ||                     ||    |     |     |
||                         || +++                                                              ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
| Load balancing algorithm | Round robin, least connections, and source IP hash                | √                     | √                   |     |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Sticky sessions         || If you enable sticky sessions, requests from the same client     || √                    || √                  ||    |     |     |
||                         || will be routed to the same backend server during the session.    ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| WebSocket protocol      || WebSocket is a new HTML5 protocol that provides full-puplex      || √                    || √                  ||    |     |     |
||                         || will be routed to the same backend server during the sessions    ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Domain name- or         || ELB allows you to add forwarding policies to forward requests    ||                       || √ (Currently, you  ||    ||    ||    |
|| URL-based forwarding    || to different backend server groups based on the domain           || _                     || can add forwarding  ||    ||    ||    |
||                         || names or URLs specified in the forwarding policies.              ||                       || policies only to    ||    |     |     |
||                         ||                                                                  ||                       || HTPP or HTTPS       ||    |     |     |
||                         ||                                                                  ||                       || listners.)          ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Adding ECSs as          || You can add ECSs to backend server groups to handle              || √                    ||                     ||    |     |     |
|| backend servers         || requests from load balancers.                                    ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Whitelist-based         || √                                                               || √                    || √                  ||    |     |     |
|| access control          ||                                                                  ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Standard OpenStack APIs || √                                                               || √                    || √                  ||    |     |     |
||                         ||                                                                  ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Adding BMSs as          || _                                                                || √                    || √                  ||    |     |     |
|| backend servers         ||                                                                  ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| SNI for certificates    || Server Name Indication (SNI) is an extension to Transport        || √                    || √                  ||    |     |     |
||                         || Layer Security (TLS) and is used in cases that a server uses     ||                       ||                     ||    |     |     |
||                         || multiple domain names and certificates. After SNI is enabled,    ||                       ||                     ||    |     |     |
||                         || certificates corresponding to the domain names are required.     ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
| SSL protocol             | Load balancers use SSL to receive requests from clients.          | √                     | —                   |     |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| OBS storage for         || Access logs of load balancers can be dumped to OBS buckets       || √                    || —                  ||    |     |     |
|| access logs             || for storage                                                      ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Server weight           || You can configure different weights for backend servers when     || —                    || √                  ||    |     |     |
||                         || you select the round robin or least connections as the load      ||                       ||                     ||    |     |     |
||                         || balancing algorithm.                                             ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Modifying certificate   || You can modify the content of a certifiocate                     || —                    || √                  ||    |     |     |
|| content                 ||                                                                  ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Mutual authencication   || The identities of both communication parties are authenticated   || —                    || √                  ||    |     |     |
||                         || to ensure security. You need to deploy both the server           ||                       ||                     ||    |     |     |
||                         || certificate and client certificate. Only HTTPS listeners support ||                       ||                     ||    |     |     |
||                         || this feature.                                                    ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| HTTP redirection        || HTTP traffic is redirected to HTTPS. When the client sends an    || —                    ||                     ||    |     |     |
||                         || HTTP request, the backend server returns an HTTPS                ||                       || √                  ||    |     |     |
||                         || reponse.                                                         ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
|| Perfromance             || Cloud Eye allows you to monitor your resources, including load   || —                    || √                  ||    |     |     |
|| monitoring on a per     || balancers.                                                       ||                       ||                     ||    |     |     |
|| listener basis          ||                                                                  ||                       ||                     ||    |     |     |
+--------------------------+-------------------------------------------------------------------+------------------------+----------------------+-----+-----+-----+
























