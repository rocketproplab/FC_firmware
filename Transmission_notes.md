Transmission Notes
==================

Buffer size when reading: 255 bytes

ID Section Size: 1 byte
*   Unique ID for each Beaglebone, as well as each sensor that generates
    large data volumes(engine sensors)

Data Section Size: 254 bytes
*   Beaglebones
    +   Divide data section into several sections, one for each sensor
    +   Tentative: 25 bytes per sensor, 8 readings per sensor
        -   Gives each beaglebone 10 sensor capacity
	-   Assumes 12 bits per reading
*   High Volume Sensors
    +   Entire data section devoted to aggregate data
    +   84 readings per transmission 
        -   12 bits per reading


Data Throughput
---------------

TODO
