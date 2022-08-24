### Flow Control

1) Flow control is a technique to control the rate of data transfer so that the
   buffer of the receiver is not overflowed.

2) Flow control is provided by the sender maintaining a variable called the 
   receive window (rwnd). 

3) The receiver computes rwnd by 
   rwnd = RcvBuffer - [LastByteRcvd - LastByteRead]
   then tells the sender the current value of rwnd in the receive window field
   of every segment it sends back to the sender. (TCP is full duplex)

4) The sender tracks LastByteSent and LastByteAcked and keeping 
   LastByteSent - LastByteAcked < rwnd, the sender is assured that it is not
   overflowing the receievers buffer.

5) The sender is allowed to send segments of one byte even when the rwnd == 0.
   This will be acked by the receiver to notify the sender when room is created
   in the buffer.