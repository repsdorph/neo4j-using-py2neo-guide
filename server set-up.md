# How to set up the server

This describs how I've set up the server. As an example throuout this guide, we will work on an Amazone M3.medium serve
(link-to-server) who has the following specifications:
- OS: Ubuntu
- RAM: 8GB
- # of CPU: 2

-- file input --
http://neo4j.com/docs/stable/linux-performance-guide.html#_setting_the_number_of_open_files

-- Configuration of RAM --
http://neo4j.com/docs/stable/server-performance.html
http://stackoverflow.com/questions/24862445/neo4j-cpu-stuck-on-gc

-- Garbage collection --
It might be a good idea to use some other GC than the default. (Find article and so on)

-- Threads --
Optimise Threads from your client to be below 80 as Neo4j Server allocated 80 threads to the JVM, so no point in sending rest calls on more than 80 threads. (This is for a machine with 8 cores (Neo4j allocated 10 threads per core)).

So if you neo4j server is a dual core (10 * 2) = 20 threads. Quad Core = 40 Threads.

Use the Rest batching API.
http://romikoderbynew.com/2011/09/23/neo4j-java-jvm-garbage-collection-profilingheap-sizelog-rotationlucene-rest-api-performance-analysis/

