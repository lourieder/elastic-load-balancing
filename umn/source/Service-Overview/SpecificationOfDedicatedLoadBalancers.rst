==========================================
Specifications of Dedicated Load Balancers
==========================================

Dedicated load balancers are available in different specifications. 
Each specification contains some key metrics from which you can decide whether the specification meets your needs. 
When the traffic exceeds the selected specifications, new requests will not be routed, 
and packet loss will occur.

   - Maximum connections

        The metric measures the maximum number of concurrent connections that a load balancer can handle.
        If the number of connections reaches that defined in the specification, 
        new requests will be discarded to ensure the performance of existing connections.

   - Connections per second (CPS)

        CPS refers to the number of new connections that a load balancer establishes with clients per second. 
        If the number reaches that defined in the specification, 
        new requests will be discarded to ensure the performance of established connections.
        When HTTPS listeners are establishing connections with clients, SSL handshakes occupy more system resources. 
        The number of new HTTPS connections per second is only 10% of the number of new HTTP connections per second.
        For example, if the specification of a load balancer is small I, 
        and the number of new HTTP connections is 10,000, 
        the number of new HTTPS connections per second is 1,000.

    - Queries per second (QPS) 
  

        QPS measures the number of HTTP or HTTPS requests sent to a backend server per second. 
        If the QPS reaches that defined in the specification,
        new requests will be discarded to ensure the performance of established connections.

Table 1 and Table 2 list the specifications of dedicated load balancers. 
(*Available specifications may vary depending on the resources in different regions.*)


..image:: catution.png

The load balancing type cannot be changed after being selected.

For example, after you have selected network load balancing, you cannot change it to application load balancing. 
If you select network load balancing, you can add only TCP and UDP listeners to the load balancer. 
If you select application load balancing, you can add only HTTP and HTTPS listeners.

*Table 1* Network load balancing (TCP/UDP)

+----------+----------------------+---------+--------------------+-------------------------+
| Type     | Maximum connections  | CPS     | Bandwidth (Mbit/s) | Number of LCUs in an AZ |
+==========+======================+=========+====================+=========================+
| Small 1  | 500,000              | 10,000  | 50                 | 10                      |
+----------+----------------------+---------+--------------------+-------------------------+
| Small 2  | 1,000,000            | 20,000  | 100                | 20                      |
+----------+----------------------+---------+--------------------+-------------------------+
| Medium 1 | 2,000,000            | 40,000  | 200                | 40                      |
+----------+----------------------+---------+--------------------+-------------------------+
| Medium 2 | 4,000,000            | 80,000  | 400                | 80                      |
+----------+----------------------+---------+--------------------+-------------------------+
| Large 1  | 10,000,000           | 200,000 | 1,000              | 200                     |
+----------+----------------------+---------+--------------------+-------------------------+
| Large 2  | 20,000,000           | 400,000 | 2,000              | 400                     |
+----------+----------------------+---------+--------------------+-------------------------+


*Table 2* Application load balancing (HTTP/HTTPS)

+----------+----------------------+-------------+-------------+------------+-------------+--------------------+-------------------------+
| Type     | Maximum connections  | CPS (HTTP)  | CPS (HTTPS) | QPS (HTTP) | QPS (HTTPS) | Bandwidth (Mbit/s) | Number of LCUs in an AZ |
+==========+======================+=============+=============+============+=============+====================+=========================+
| Small 1  | 200,000              | 2,000       | 200         | 4,000      | 2,000       | 50                 | 10                      |
+----------+----------------------+-------------+-------------+------------+-------------+--------------------+-------------------------+
| Small 2  | 400,000              | 4,000       | 400         | 8,000      | 4,000       | 100                | 20                      |
+----------+----------------------+-------------+-------------+------------+-------------+--------------------+-------------------------+
| Medium 1 | 800,000              | 8,000       | 800         | 16,000     | 8,000       | 200                | 40                      |
+----------+----------------------+-------------+-------------+------------+-------------+--------------------+-------------------------+
| Medium 2 | 2,000,000            | 20,000      | 2,000       | 40,000     | 20,000      | 400                | 80                      |
+----------+----------------------+-------------+-------------+------------+-------------+--------------------+-------------------------+
| Large 1  | 4,000,000            | 40,000      | 4,000       | 80,000     | 40,000      | 1,000              | 200                     |
+----------+----------------------+-------------+-------------+------------+-------------+--------------------+-------------------------+
| Large 2  | 8,000,000            | 80,000      | 8,000       | 160,000    | 80,000      | 2,000              | 400                     |
+----------+----------------------+-------------+-------------+------------+-------------+--------------------+-------------------------+


..image::note.png 

- If you add multiple listeners to a load balancer,
        the sum of QPS values of all listeners cannot exceed the QPS defined in each specification.

    - The bandwidth is the upper limit of the sum of the inbound traffic and outbound  traffic.
        For example, for a small I dedicated load balance the sum of the inbound traffic
        and outbound traffic must be less than or equal to 50 Mbit/s.

    - If you select more than one AZ when you create a dedicated load balancer,
        the number of new connections and the number of concurrent connections it can handle will be double.
        For example, if you deploy a dedicated load balancer in two AZs, 
        it can handle up to 40 million concurrent connections.
