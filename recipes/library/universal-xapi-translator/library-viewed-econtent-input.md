This is the input file for an library-viewed-econtent event.

Data should be supplied as a UTF-8 Tab Seperated File called econtent.tsv

# library-viewed-econtent

* [USERNAME](#username) [1]
* [CLIENT_IP](#client_ip) [1]
* [SESSION_ID](#session_id) [1]
* [TIMESTAMP](#timestamp) [1]
* [HTTP_REQUEST](#http_request) [1]
* [HTTP_RESPONSE](#http_response) [0..1]
* [BYTES_DOWNLOADED](#bytes_downloaded) [0..1]
* [EZPROXY_GROUP_MEMBERSHIP](#ezproxy_group_membership) [0..1]
* [HTTP_REFERRER](#http_referrer) [0..1]
* [HTTP_BROWSER_INFO](#http_browser_info) [0..1]


## USERNAME 
### Description

A unique identifier for that user

### Purpose

Analytics - to identify that user

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)

## CLIENT_IP 
### Description

Client's address location on internet

### Purpose

Analytics - to identify the access location

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)


## SESSION_ID
### Description

tbc

### Purpose

tvc

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)

## TIMESTAMP
### Description

Timestamp representing time

### Purpose

Analytics - Identify time in which resources are accessed.

### Derivation
Jisc

### Valid Values
Any

### Format
ISO 8601 timestamp


## HTTP_REQUEST
### Description

tbc
### Purpose

tbc

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)

## HTTP_RESPONSE
### Description

tbc

### Purpose

tbc

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)


## BYTES_DOWNLOADED
### Description

tbc

### Purpose

tbc

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)


## EZPROXY_GROUP_MEMBERSHIP
### Description

tbc

### Purpose

tbc

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)

## HTTP_BROWSER_INFO
### Description

tbc

### Purpose

tbc

### Derivation
Jisc

### Valid Values
Any

### Format
String (255)
