This is the specification for an input TSV file for logging in events.

Data should be supplied as a UTF-8 Tab Separated File called login.tsv

# login

* [USERNAME](#username) [1]
* [HOMEPAGE](#homepage) [1]
* [CLIENT_IP](#client_ip) [1]
* [PLATFORM](#platform) [1]
* [TIMESTAMP](#timestamp) [1]
* [SESSION_ID](#session_id) [0..1]
* [OBJECT_ID](#object_id) [1]
* [OBJECT_NAME](#object_name) [0..1]
* [SUBTYPE](#subtype) [0..1]

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
An identifier for the application being logged in to.

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

## SUBTYPE 
### Description
Used to identify the subType of the application that is being logged into

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
iri