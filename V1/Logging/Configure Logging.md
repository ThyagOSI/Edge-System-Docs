---
uid: loggingConfiguration
---

# Message logging configuration
Edge System writes daily log messages to flat text files in the following locations:

• Windows: *%ProgramData%/OSIsoft/EdgeSystem/Logs*

• Linux: */usr/share/OSIsoft/EdgeSystem/Logs*

Each message in the log displays the message severity level, timestamp, and the message itself.

## Change logging levels

By default, logging captures Information, Warning and Error and Critical messages in the message logs.

The schema file specifies how to formally describe the configuration parameters for message logging. 

It is located in:

• Windows: *%ProgramFiles%/OSIsoft/EdgeSystem/Schema*

• Linux: */opt/EdgeSystem/Schema*

**Note:** 

The individual components of Edge System have their own logging files, for example:
◦ Modbus TCP connectivity: Modbus1_Logging.json
◦ OPC UA connectivity: OpcUa1_Logging.json
◦ Edge Data Store (EDS): Storage_Logging.json

To adjust this behavior, perform the following:
