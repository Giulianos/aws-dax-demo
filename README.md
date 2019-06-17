# AWS DAX Demo

This is an example app provided by AWS to compare
DynamoDB performance with and without DAX.

## Results

### Without DAX

```
Creating a DynamoDB client
Creating table...
Attempting to create table; please wait...
Successfully created table.  Table status: ACTIVE
Populating table...
Writing data to the table...
Writing 10 items for partition key: 1
Writing 10 items for partition key: 2
Writing 10 items for partition key: 3
Writing 10 items for partition key: 4
Writing 10 items for partition key: 5
Writing 10 items for partition key: 6
Writing 10 items for partition key: 7
Writing 10 items for partition key: 8
Writing 10 items for partition key: 9
Writing 10 items for partition key: 10
Running GetItem, Scan, and Query tests...
First iteration of each test will result in cache misses
Next iterations are cache hits

GetItem test - partition key 1 and sort keys 1-10
	Total time: 56.492 ms - Avg time: 5.649 ms
	Total time: 44.731 ms - Avg time: 4.473 ms
	Total time: 46.684 ms - Avg time: 4.668 ms
	Total time: 43.864 ms - Avg time: 4.386 ms
	Total time: 52.242 ms - Avg time: 5.224 ms
Query test - partition key 5 and sort keys between 2 and 9
	Total time: 11.929 ms - Avg time: 2.386 ms
	Total time: 6.774 ms - Avg time: 1.355 ms
	Total time: 6.221 ms - Avg time: 1.244 ms
	Total time: 5.709 ms - Avg time: 1.142 ms
	Total time: 5.710 ms - Avg time: 1.142 ms
Scan test - all items in the table
	Total time: 46.084 ms - Avg time: 9.217 ms
	Total time: 28.213 ms - Avg time: 5.643 ms
	Total time: 21.227 ms - Avg time: 4.245 ms
	Total time: 17.167 ms - Avg time: 3.433 ms
	Total time: 34.851 ms - Avg time: 6.970 ms

Attempting to delete table; please wait...
Successfully deleted table.
```

### With DAX

```
Creating a DynamoDB client
Creating a DAX client with cluster endpoint mydaxcluster.xocfgp.clustercfg.dax.usw2.cache.amazonaws.com:8111
Jun 17, 2019 12:03:04 AM com.amazon.dax.client.cluster.Cluster startup
INFO: connected to cluster endpoints: [Backend{addr=/172.31.58.104:8111,healthy=true,active=true,config=ServiceEndpoint{75809965,null,[-84, 31, 58, 104],8111,LEADER,us-west-2b,713040381101}}]
Creating table...
Attempting to create table; please wait...
Successfully created table.  Table status: ACTIVE
Populating table...
Writing data to the table...
Writing 10 items for partition key: 1
Writing 10 items for partition key: 2
Writing 10 items for partition key: 3
Writing 10 items for partition key: 4
Writing 10 items for partition key: 5
Writing 10 items for partition key: 6
Writing 10 items for partition key: 7
Writing 10 items for partition key: 8
Writing 10 items for partition key: 9
Writing 10 items for partition key: 10
Running GetItem, Scan, and Query tests...
First iteration of each test will result in cache misses
Next iterations are cache hits

GetItem test - partition key 1 and sort keys 1-10
	Total time: 848.800 ms - Avg time: 84.880 ms
	Total time: 10.621 ms - Avg time: 1.062 ms
	Total time: 8.128 ms - Avg time: 0.813 ms
	Total time: 6.635 ms - Avg time: 0.663 ms
	Total time: 8.217 ms - Avg time: 0.822 ms
Query test - partition key 5 and sort keys between 2 and 9
	Total time: 113.261 ms - Avg time: 22.652 ms
	Total time: 2.410 ms - Avg time: 0.482 ms
	Total time: 2.190 ms - Avg time: 0.438 ms
	Total time: 3.855 ms - Avg time: 0.771 ms
	Total time: 1.847 ms - Avg time: 0.369 ms
Scan test - all items in the table
	Total time: 64.409 ms - Avg time: 12.882 ms
	Total time: 8.898 ms - Avg time: 1.780 ms
	Total time: 7.771 ms - Avg time: 1.554 ms
	Total time: 7.610 ms - Avg time: 1.522 ms
	Total time: 10.517 ms - Avg time: 2.103 ms

Attempting to delete table; please wait...
Successfully deleted table.
```
