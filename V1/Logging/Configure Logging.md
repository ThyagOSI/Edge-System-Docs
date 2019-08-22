---
uid: loggingConfiguration
---

# Message logging configuration
Edge System writes daily log messages to flat text files in the following locations:

• Windows: *%ProgramData%/OSIsoft/EdgeSystem/Logs*
• Linux: */usr/share/OSIsoft/EdgeSystem/Logs*

Each message in the log displays the message severity level, timestamp, and the message itself.

## Default logging configuration and Schema
By default, logging captures Information, Warning and Error and Critical messages in the message logs.
The default logging configuration for a component on install is 
```json
{
  "logLevel": "Information",
  "logFileSizeLimitBytes": 34636833,
  "logFileCountLimit": 31   
}
```

The schema file specifies how to formally describe the configuration parameters for message logging. 
It is located in:

• Windows: *%ProgramFiles%/OSIsoft/EdgeSystem/Schema*
• Linux: */opt/EdgeSystem/Schema*

**Note:** 

The individual components of Edge System have their own logging files, for example:
• Modbus TCP connectivity: Modbus1_Logging.json
• OPC UA connectivity: OpcUa1_Logging.json
• Edge Data Store (EDS): Storage_Logging.json

### Changing logging configuration
To change the logging configuration you can save the JSON containing the information in the JSON format a file named Component_Logging.json and run the following script:

```bash
curl -i -d "@Component_Logging.json" -H "Content-Type: application/json" -X PUT http://localhost:5590/api/v1/configuration/ConnectivityId/Logging
```

After the REST command completes, the logging configuration change is auto detected and takes effect during runtime.