### Congestion Control

1) Congestion control is needed to prevent the sender from congesting the
   network by keep sending data packets.

2) Congestion control is provided by the sender maintaining a variable called
   the congestion window (cwnd). Together with receive window (rwnd) used for
   flow control, the sender makes sure the below is satisfied.
   LastByteSent – LastByteAcked <= min{cwnd, rwnd}

3) The overall algorithm can be explained by transitions between three different
   modes, namely slow start, congestion avoidance and fast recovery.

4) Fast recovery is a recommended, but not required, component of TCP. TCP Tahoe
   does not have it while the newer TCP Reno incorporated fast recovery.

5) The transmission round - congestion window graph gives a sawtooth pattern.
   (exponential increase - linear increase - drop back to cwnd = 1)

### Slow Start

1) Slow start is a phase of TCP during which the sender starts sending data
   packets at a very low rate but increases the rate exponentially until it
   encounters the first sign of congestion.

2) cwnd begins at 1 MSS (maximum segment size) and increases by 1 MSS for every
   ACK received. (Therefore, 1 -> 2 -> 4 -> 8 -> 16 -> 32 -> 64 -> ...)

3) When there is a loss event indicated by a timeout from the sender, the sender
   reduces the cwnd by 1 MSS and begins the slow start process anew. It also
   sets the ssthresh(slow start threshold) to half the cwnd
   (sshthresh = cwnd/2)

4) When the cwnd reaches the ssthresh, the sender enters the congestion
   avoidance phase.

### Congestion Avoidance

1) Congestion avoidance is a phase of TCP where it increases the cwnd value
   linearly as opposed to exponentially as in the slow start phase. (1 MSS per
   RTT)

2) When a timeout occurs cwnd is set to 1 MSS and the value of ssthresh is set
   to cwnd/2 just like in the slow start phase.

3) When a triple duplicate ACK is received, cwnd is set to cwnd/2 + 3
   (cwnd = cwnd/2 + 3), and the ssthresh is set to cwnd/2. For TCP Reno, it
   enters the fast-recovery state. For TCP Tahoe, it enters the slow start
   phase (cwnd = 1, ssthresh = cwnd/2).

### Fast Recovery

1) Fast recovery is a phase where it keeps the cwnd value high until a timeout
   event occurs to keep the overall throughput high.

2) cwnd is increased by 1 MSS for every duplicate ACK received for the missing 
   segment that caused TCP to enter the fast recovery phase.

3) When ACK arrives for the missing segment, TCP enters the congestion avoidance
   phase.

4) If a timeout event occurs, TCP enters the slow start phase.

