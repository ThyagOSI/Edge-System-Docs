---
uid: loggingConfiguration
---

# Message logging configuration
Edge System writes daily log messages to flat text files in the following locations:

• Windows: *%ProgramData%/OSIsoft/EdgeSystem/Logs*

• Linux: */usr/share/OSIsoft/EdgeSystem/Logs*

Each message in the log displays the message severity level, timestamp, and the message itself.

The individual components of Edge System have their own logging files located in the configuration folder, for example:

• Windows: *%ProgramData%/OSIsoft/EdgeSystem/Configuration*

• Linux: */usr/share/OSIsoft/EdgeSystem/Configuration*

• Modbus TCP connectivity: Modbus1_Logging.json

• OPC UA connectivity: OpcUa1_Logging.json

• Edge Data Store (EDS): Storage_Logging.json

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

Changing the logLevel leads to captures of logs in severity including and above the specified log level. The log levels in their increasing order of severity are as follows: Trace, Debug, Information, Warning, Error, Critical.

The logFileCountLimit controls the number of days the log files are persisted before they are deleted for creation of new log files. 

## Changing logging configuration
To change the logging configuration you can save the new configuration information in a JSON file format and run the following script (or make an equivalent REST API call)

E.g. Component_Logging.json
```json
{
  "logLevel": "Warning",
  "logFileSizeLimitBytes": 16777216,
  "logFileCountLimit": 30   
}
```


```bash
curl -i -d "@Component_Logging.json" -H "Content-Type: application/json" -X PUT http://localhost:5590/api/v1/configuration/<ComponentId>/Logging
```

where \<ComponentId> is the ComponentId of the adapter or Storage.

On successful execution, the logging configuration change takes effect immediately during runtime.

### **Note:** 
If you do not specify *all* the parameters while changing the configuration, it will result in specified parameter(s) getting updated while the unspecified parameter(s) reverting to the default schema values. 
