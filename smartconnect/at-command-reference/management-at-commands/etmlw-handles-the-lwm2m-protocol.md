# ETMLW – handles the LwM2M protocol

Manages the LwM2M protocol, which enables you to add, delete and update LwM2M resource values. Before you can use ETMLW, ensure that you have enabled the LwM2M protocol using AT+ETMSTATE="startlwm2m". For more information, see ETMSTATE – check current state.

| Type  | Syntax                                                                                                                                                             | Response                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Test  | AT+ETMLW=?                                                                                                                                                         | +ETMLW: "add",,,, +ETMLW: "remove",\<id                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Read  | AT+ETMLW? – returns the current list of user resources, which were added using AT+ETMLW="add"..., as well as resources specified in the lwm2m\_resources.ini file. | +ETMLW: ,,, +ETMLW: ,,, ... OK where: - id – the unique identifier for the LwM2M resource - uri – the unique URI for the LwM2M resource - datatype – the data format (either "Integer", "String", or "Boolean"). - – indicates the resource status, either: - "adding" – waiting to register the resource on the server - "removing" – waiting to de-register (delete) the resource from the server - "ready" – resource registered on the server or ERROR |
| Write | AT+ETMLW= where is either: - "add",,,, – adds a new LwM2M resource. - "remove",\<id                                                                                | "uri"> – deletes the current LwM2M resource. - "update",\<id                                                                                                                                                                                                                                                                                                                                                                                               |

#### Example

```
AT+ETMLW="add",-1,"/32769/0/1","Integer",123
OK
+ETMLW: 0,"/32769/0/1","ADD",0
```

```
AT+ETMLW="add",-1,"/32769/1/1","String","Temp: 17°C"
OK
+ETMLW: 0,"/32769/1/1","ADD",-12
```

```
AT+ETMLW="add",-1,"/32769/1/1","Integer",17
OK
+ETMLW: 1,"/32769/1/1","ADD",0
```

```
AT+ETMLW?
+ETMLW: 0,"/32769/0/1","integer","ready"
+ETMLW: 1,"/32769/1/1","integer","ready"
OK
```
