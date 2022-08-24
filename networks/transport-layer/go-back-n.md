### Characteristics

1) Sender is allowed to transmit multiple packets without waiting for ACKs. This
   is to improve throughput via pipelining.
2) The maximum allowable number of packets that can be traveling is bounded by N.
3) N is often referred to as the window size. GBN protocol itself as a sliding
   window protocol.

### Receiver

1) For seq number in [rcv_base, rcv_base+N-1]
   Acknowledges uncorrupted packets whether or not it is in order. If sequence
   number is bigger than rcv_base, packets are buffered until lower sequence
   number packets are received. After the gap has been filled between rcv_base
   and buffered packets, they are all sent to the upper layer together and the 
   rcv_base is updated.
2) For seq number in [rcv_base-N, rcv_base-1]
   If a packet seq number is smaller than rcv_base, ACK must be still generated
   so the sender can continue sending the next packet.
3) Otherwise, discard the packet.

### Sender

1) Upon receipt of data from upper layer, the sender sends the data to the
   receiver if nextseqnum < base + N (window size limit). Otherwise it is
   buffered or returned to the upper layer.
2) Upon receipt of ACK from receiver, check corruption with checksum. If it's
   corrupted, do nothing. If it's not corrupted, update the base to acknum + 1.
   If base == nextseqnum, stop timer. Otherwise, restart timer.
3) Upon ACK receipt, the sender marks the packet as ACKed provided its in the
   window. If the sequence number is equal to send_base, window's base is 
   updated and window is moved forward.
