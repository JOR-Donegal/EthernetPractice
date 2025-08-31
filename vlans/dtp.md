# DTP

There is a Cisco proprietary protocol which allows switches to negotiate trunk links and the type of encapsulation. You should always switch this off using the command **switchport nonegotiate**.

At the end of a configuration, it can be useful to look at the command **show int gi0/1** **switchport** to see a summary of the important layer 2 data.

If you are doing a Wireshark capture, you will see protocols like VTP and CDP classified as DTP protocols.
