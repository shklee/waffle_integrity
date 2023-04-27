# Waffle

Waffle is the first system to hide data access patterns adaptively, without requiring to
known the input data access distribution, under a passive persistent
adversary. Waffle incurs a constant bandwidth and client-side storage
overhead, both of which can be configured by an application
owner.

## Requirements

* cmake-3.5+
* redis-server (https://redis.io/docs/getting-started/installation/install-redis-on-linux/ )

## Building

After installing the requirements, run

```
sh build.sh
```
inside waffleClient folder

## Running 

Running Waffle requires atleast 3 machines:

1. Client with a CLIENT_IP and CLIENT_PORT
2. Proxy with a PROXY_IP
3. Redis backing storage server with STORAGE_SERVER_IP and STORAGE_PORT

First start the storage server

Then start the proxy:

```
./bin/proxy_server  -l <WORKLOAD_FILE> -b <BATCH_SIZE> -r <SYSTEM_PARAMETER> -f <FAKE_QUERIES_FOR_DUMMY_OBJECTS> -d <NUMBER_OF_DUMMY_OBJECTS> -c <CACHE_SIZE> -n <NUM_CORES> -h <STORAGE_SERVER_IP> -p <STORAGE_PORT>
```

Waffle will now initialize. After the proxy says it's reachable launch the benchmark code:

```
./bin/proxy_benchmark -t <TRACE_FILE> -h <PROXY_IP> -p <PROXY_PORT> -n <NUM_CLIENTS>
```

After completion the benchmark will display the throughput during the run. There will be a new folder in the data folder that contains one file for each client displaying the latency of each operation in nanoseconds.
