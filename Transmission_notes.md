Transmission Notes
==================

All data will be transmitted over streams

*   Beaglebones
    +   Buffer size: 255 bytes
    +   Divide data section into several sections, one for each sensor
    +   Cycle sends reading for each sensor sequentially
    +   Tentative: 32 bits per sensor, 64 sensor capacity
        -   Assumes 12 bits per reading
        -   16 bits for timestamp
        -   4 bits buffer 
    +   Without buffer: 28 bits per sensor, 72 sensor capacity
        -   12 bits per reading
        -   16 bits for timestamp

*   High Volume Sensors
    +   Buffer size: 1023 bytes
        -   Must set SO_RCVBUF using setsockopt
    +   Has own process and own socket
    +   Entire data section devoted to aggregate data
    +   256 readings per buffer read cycle, each reading is 32 bits
        -   12 bits per reading
        -   16 bits for timestamp
        -   4 bits of buffer
    +   Without buffer: 288 readings per buffer cycles, each reading 28 bits
        -   12 bits per reading
        -   16 bits for timestamp

Misc
----
*   Set SO_REUSEADDR to be able to reuse sockets

*   Times will be stored as 16 bit (unsigned?) shorts, and are the time elapsed
    since timekeeping was started at the beginning of the program.
    -   That original time should be sent in the very first transmission 
        establishing connection integrity

*   Relevant man pages: tcp, socket, ip


NOTE: can increase buffer size if needed to reduce data backlog

Data Throughput
---------------

TODO
