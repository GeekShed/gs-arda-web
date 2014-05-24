/*
Title: HAVOK protocol
*/

# HAVOK protocol design document.

This page describes version 0.1 of the Havok protocol.


##Packet Format: (all integers are in network byte order)
<pre>
+---------------------------------------------------------------+
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
+---------------------------------------------------------------+
|                          Server ID                            |
+---------------------------------------------------------------+
|                          Flags                                |
+---------------------------------------------------------------+
|                          Serial                               |
+---------------------------------------------------------------+
|                      Serial - continued                       |
+---------------------------------------------------------------+
|                       Target Length                           |
+---------------------------------------------------------------+
|                       Message Length                          |
+---------------------------------------------------------------+
|                          Target                               |
+---------------------------------------------------------------+
|                            ...                                |
+---------------------------------------------------------------+
|                          Message                              |
+---------------------------------------------------------------+
|                            ...                                |
+---------------------------------------------------------------+
</pre>

Currently only 1 flag is defined:


1. State 

	On - Serial number has meaning

	Off - Serial number has no meaning. 

##Operation
Each HAVOK node connects to every other HAVOK node. Each node 'knows' the connection profiles of every other havok node via a configuration file. This connection profile is essentially ip/port pairs and each server id. This server id is used to differentiate connections as well as for determining what to play back on reconnection. We keep the most recently received serial number in the daemon, and use that to 