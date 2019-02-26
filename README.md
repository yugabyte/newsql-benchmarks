# NewSQL Benchmark Suite

This benchmark suite tests various NewSQL style workloads such as:
* Single key-value inserts, updates and queries
* Batch inserts and short-range scans
* Inserts into a table with secondary indexes and lookups by the index
* Distributed transactions involving mult-key updates

## Workloads Types

The sample apps here have drivers compatible with the above and emulate a number of workloads.

| Workload Type              | Workloads                    |
| -------------------------- | ---------------------------- |
| Inserts and queries        | CrSqlInserts, YbCqlInserts   |
| Updates and queries        | CrSqlUpdates                 |
| Secondary index operations | CrSqlSecondaryIndex          |
| Distributed transactions   | CrSqlSnapshotTxns            |

## Running the benchmark suite

For help, simply run the following:

```
$ java -jar target/newsql-benchmarks.jar \
      --nodes 127.0.0.1:9042             \
      --workload YbYcqlInserts           \
      --value_size 5000
```

Other options (with default values):
```
  --num_unique_keys 1000000
  --num_reads -1
  --num_writes -1
  --value_size 1024
  --num_threads_read 24
  --num_threads_write 2
  --table_ttl_seconds -1
```

## Building the benchmark suite

You need the following to build:
* Java 1.8 or above
* Maven version 3.3.9 or above

To build, simply run the following:
```
$ mvn -DskipTests package
```

You can find the executable one-jar at the following location:
```
$ ls target/newsql-benchmarks.jar
target/newsql-benchmarks.jar
```

To docker image with the package, simply run the following:
```
$ mvn package
```
