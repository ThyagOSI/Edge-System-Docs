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

The individual components of Edge System have their own logging files, for example:

• Modbus TCP connectivity: Modbus1_Logging.json

• OPC UA connectivity: OpcUa1_Logging.json

• Edge Data Store (EDS): Storage_Logging.json

## Changing logging configuration
To change the logging configuration you can save the new configuration information in a JSON format a file (E.g. Component_Logging.json) and run the following script or make an equivalent REST API call:

```bash
curl -i -d "@Component_Logging.json" -H "Content-Type: application/json" -X PUT http://localhost:5590/api/v1/configuration/<ComponentId>/Logging
```

where \<ComponentId> is the ComponentId of the adapter or Storage.

After the REST command completes, the logging configuration change is auto detected and takes effect during runtime.

### **Note:** 
If you do not specify *all* the Schema parameters while changing the configuration, it will result in specified parameter(s) getting updated while the unspecified parameter(s) reverting to the default schema values. 
