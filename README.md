# CS340 Traceroute Programming Project

## Overview

This project extends a raw socket ICMP ping implementation to create a
Traceroute diagnostic tool. The program sends ICMP echo requests with
increasing Time-To-Live (TTL) values to identify the sequence of routers
between the source host and a destination host.

As packets travel through the network, routers return ICMP Time Exceeded
messages when the TTL reaches zero. By collecting these responses, the
program determines the path taken by packets and measures the round-trip
time (RTT) for each hop.

## Learning Outcomes

-   Working with raw sockets in Python
-   Understanding ICMP packet structure and message types
-   Implementing packet validation and error handling
-   Measuring network latency and packet loss
-   Implementing traceroute functionality using TTL values

## Files

-   `IcmpHelperLibrary.py`\
    Python implementation of ICMP ping and traceroute functionality.

-   `Traceroute.pdf`\
    Project report describing the implementation and example output.

## Components

### ICMP Packet Validation

The program validates received ICMP echo replies by comparing the
identifier, sequence number, and raw data against the values sent in the
original request. Debug messages report expected and actual values to
confirm packet integrity.

### Ping Statistics

The program calculates network statistics similar to the standard ping
utility, including:

-   Minimum round-trip time (RTT)
-   Maximum round-trip time (RTT)
-   Average round-trip time (RTT)
-   Packet loss percentage

### ICMP Error Handling

The implementation parses ICMP response types and codes, including
common responses such as:

-   Echo Reply (Type 0)
-   Destination Unreachable (Type 3)
-   Time Exceeded (Type 11)

These responses are displayed in a human-readable format for easier
diagnostics.

### Traceroute Functionality

Traceroute is implemented by sending ICMP echo requests with
incrementally increasing TTL values. Each router that processes the
packet returns an ICMP response, allowing the program to identify the
path taken to the destination host and measure the latency for each hop.

## Notes

Running the program requires raw socket access, which may require
administrator or root privileges depending on the operating system.
