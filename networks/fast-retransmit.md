### Characteristics

1) One of the problems with timeout-triggered retransmissions is that the
   timeout period can be relatively long. When a segment is lost, this long
   timeout period forces the sender to delay resending the lost packet, thereby
   increasing the end-to-end delay. Fortunately, the sender can often detect
   packet loss well before the timeout event occurs by noting so-called
    duplicate ACKs.
2) The sender waits for three duplicate ACK before fast retransmit. It is
   assumed that if there is just a reordering of the segments, there will be
   only one or two duplicate ACKs before the reordered segment is processed,
   which will then generate a new ACK. If three or more duplicate ACKs are
   received in a row, it is a strong indication that a segment has been lost.
