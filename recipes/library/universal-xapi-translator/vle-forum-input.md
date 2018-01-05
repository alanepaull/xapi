This is the specification for an input TSV file for logging in events.

Data should be supplied as a UTF-8 Tab Separated File called forum.tsv

# login

* [TIMESTAMP](#timestamp) [1]
* [USERNAME](#username) [1]
* [HOMEPAGE](#homepage) [1]
* [ACTION](#action) [1]
* [ACTION_DISPLAY](#action_display) [1]
* [CLIENT_IP](#client_ip) [1]
* [PLATFORM](#platform) [1]
* [TIMESTAMP](#timestamp) [1]
* [SESSION_ID](#session_id) [0..1]
* [OBJECT_ID](#object_id) [1]
* [OBJECT_NAME](#object_name) [0..1]
* [FORUM_AREA](#object_id) [1]
* [VLE_MOD_ID](#vle_mod_id) [0..1]
* [UDD_MOD_INST_ID](#udd_mod_inst_id) [0..1]



## TIMESTAMP 
### Description
The time at which the user logged in to the platform

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
ISO 8601 date time

## USERNAME 
### Description
A unique identifier for the individual logging in.

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
String (256)


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
The time at which the user logged in to the platform

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
An identifier for the forum post.

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
Optional name of application being logged in to.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)

## FORUM_AREA 
### Description
Identifies the parent forum via uri.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
uri

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
The value should correspond to the UDD module_instance.MOD_INSTANCE_ID identifier for the relevant module in the UDD data.

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)

### Notes
Mandatory if VLE_MOD_ID not present.
