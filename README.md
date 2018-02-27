### Trace files for buffer mechanism testing ###

- read-after-write: do writes immediately followed by reads at the same
  location, the read write pattern is like this: W1R1W2R2W3R3.. meaning here
  first write (W) to location 1, then read (R) location 1, etc. This trace
  makes sure the reads always hit the buffer, thus you should observe very low
  read latency

- random-read: do random reads, no buffer hit in this case, thus you should
  observe read latency larger than read-after-write trace.

- write-same: write the same location for many times, in this case, you always
  see a write hit in the buffer, thus the write latency should be very small.

- write-large-random: write random large IOs, in this case, all the writes
  cannot fit into the buffer, buffer flush is triggered, thus you should
  observe varialbe write latencies.
