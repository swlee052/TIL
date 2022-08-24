### Characteristics

1) Sender is allowed to transmit multiple packets without waiting for ACKs. This
   is to improve throughput via pipelining.
2) The maximum allowable number of packets that can be traveling is bounded by N.
3) N is often referred to as the window size.
4) The receiver - sender model explained below is a one-way transfer of data,
   but actual TCP is a two-way transfer. The model below simplifies the 
   explanation.

### Receiver

1) If a packet received is in order (i.e. 0 ~ n-1 has been already received and
   the n-th packet arrived), it sends an ACK to the sender and delivers the data
   to upper layer.
2) If a packet received is out of order, it resends an ACK for the most recently
   received in-order packet to the sender and
   discards the packet.

### Sender

1) Upon receipt of data from upper layer, the sender sends the data to the
   receiver if nextseqnum < base + N (window size limit).
2) Upon receipt of ACK from receiver, check corruption with checksum. If it's
   corrupted, do nothing. If it's not corrupted, update the base to acknum + 1.
   If base == nextseqnum, stop timer. Otherwise, restart timer.
3) Upon timeout, resend all packets in the window that are not yet ACKed and
   restart timer. (this causes unnecessary retransmissions, which is a downside 
   of GBN. SR does not have this problem)
