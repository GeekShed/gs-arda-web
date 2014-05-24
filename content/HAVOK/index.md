/*
Title: HAVOK protocol
*/

## HAVOK protocol design document.

### Messages

Messages are seperated into two groups, state, and non-state. State messages have a serial number, that is automatically incremented. These serial numbers are tied to the server id number, so that serverid-serial are unique for every message. The id number is stored in a 32bit unsigned integer, which is rolled over once it overflows.