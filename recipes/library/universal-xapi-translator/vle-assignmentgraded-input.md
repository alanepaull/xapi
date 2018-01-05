This is the specification for an input TSV file for assignment graded events.

Data should be supplied as a UTF-8 Tab Separated File called assignmentgraded.tsv

# assignmentgraded


* [USERNAME](#username) [1]
* [HOMEPAGE](#homepage) [1]
* [CLIENT_IP](#client_ip) [1]
* [PLATFORM](#platform) [1]
* [SESSION_ID](#session_id) [0..1]
* [OBJECT_ID](#object_id) [1]
* [OBJECT_NAME](#object_name) [0..1]
* [VLE_MOD_ID](#vle_mod_id) [0..1]
* [UDD_MOD_INST_ID](#udd_mod_inst_id) [0..1]
* [SCORE_SCALED](#score_scaled) [0..1]
* [SCORE_RAW](#score_raw) [0..1]
* [SCORE_MIN](#score_min) [0..1]
* [SCORE_MAX](#score_max) [0..1]
* [SCORE_RESPONSE](#score_response) [0..1]
* [GRADE](#grade) [0..1]
* [DUE_DATE](#due_date) [0..1]
* [INSTRUCTOR_USERNAME](#instructor_username) [1]
* [INSTRUCTOR_HOMEPAGE](#instructor_homepage) [1]


## USERNAME 
### Description

A unique identifier for the individual whose work has been graded.

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
ip address

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

An identifier for the assignment being graded.

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

Optional name for the assignment being graded.

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)

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

## SCORE_SCALED 
### Description

The score related to the experience as modified by scaling and/or normalization. If the raw value can be calculated as a percentage then the scaled may be populated as such. In the example shown, there is a 100 question quiz and a user has 25 questions correct, corresponding to a raw value of ‘25’ and a scaled value of ‘0.25’ (25%). If the data is not scaled then it should not be given and should not be zero

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Decimal number between -1 and 1, inclusive.

### Format
single

## SCORE_RAW
### Description

Unmodified score. If not present then grade must be given.

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Decimal number between min and max

### Format
single

### Notes
Only 1 of SCORE_RAW or GRADE should be given.


## SCORE_MIN
### Description

The lowest possible score. If known this should be given.

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Decimal number less than max

### Format
single

## SCORE_MAX
### Description

The highest possible score. If known this should be given.

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Decimal number greater than min

### Format
single

## SCORE_RESPONSE
### Description

Instructor's or automatic feedback
### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)

## GRADE
### Description
Non-numerical assessment result. If not present then score_raw must be given.

### Purpose
Analytics

### Derivation
Jisc

### Valid Values
String (256)

### Format
single

### Notes
Only 1 of SCORE_RAW or GRADE should be given.

## DUE_DATE
### Description

Indicates when the assignment is due

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
ISO 8601 date time

## INSTRUCTOR_USERNAME
### Description

Login ID for the instructor

### Purpose

Analytics

### Derivation
Jisc

### Valid Values
Any

### Format
String (256)

## INSTRUCTOR_HOMEPAGE
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
