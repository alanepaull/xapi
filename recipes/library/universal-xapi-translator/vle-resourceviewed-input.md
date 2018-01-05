This is the specification for an input TSV file for viewing a vle resource.

Data should be supplied as a UTF-8 Tab Seperated File called resourceviewed.tsv

# resource_viewed

* [USERNAME](#username) [1]
* [HOMEPAGE](#homepage) [1]
* [CLIENT_IP](#client_ip) [1]
* [PLATFORM](#platform) [1]
* [TIMESTAMP](#timestamp) [1]
* [SESSION_ID](#session_id) [0..1]
* [OBJECT_ID](#object_id) [1]
* [OBJECT_NAME](#object_name) [0..1]
* [SUBTYPE](#subtype) [0..1]
* [VLE_MOD_ID](#vle_mod_id) [0..1]
* [UDD_MOD_INST_ID](#udd_mod_inst_id) [0..1]


## USERNAME 
### Description
A unique identifier for the individual viewing the resource.

### Purpose
Analytics - to identify the user

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)


## HOMEPAGE 
### Description
URL of the home page of the application for which the login id applies.

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)


## CLIENT_IP 
### Description
Client's IP address. An IPv4 address is recommended.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)


## PLATFORM 
### Description
The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard".

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)


## TIMESTAMP 
### Description
The time at which the user viewed the resource.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
ISO 8601 date time


## SESSION_ID 
### Description
The VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)


## OBJECT_ID 
### Description
An identifier for the resource being viewed.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
iri


## OBJECT_NAME 
### Description
Optional name for resource being viewed.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)


## SUBTYPE 
### Description
Used to identify the subType of the resource being viewed.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
iri


## VLE_MOD_ID 
### Description
An identifier for a course area in a VLE. It is used in conjunction with UDD_MOD_INST_ID to link module instances to course areas. Note that several module instances identified by their UDD_MOD_INST_ID can link to one VLE_MOD_ID in the VLE.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)

### Notes
Mandatory if UDD_MOD_INST_ID not present.


## UDD_MOD_INST_ID 
### Description
An identifier for a module instance
The value should correspond to the UDD module_instance.MOD_INSTANCE_ID identifier that identifies the relevant module in UDD compliant data.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)

### Notes
Mandatory if VLE_MOD_ID not present.
