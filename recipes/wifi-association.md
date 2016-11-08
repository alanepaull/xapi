---
layout: home
---

# wifi_access_recipe
Revision: 0.2

## Purpose
This activity records a users device accessing wifi via an access point.

## Definition

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](../common_structures.html#actora) page.
The actor entity describes the individual accessing wifi.


``` Javascript
"actor": {
  "objectType": "Agent",
  "name": "John Smith",
  "account": {
    "name": "jsmith12",
    "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
  }
}
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](../common_structures.html#verba) page.

The Verb, accessed, describes the action of associating a device to a wifi access point.


``` javascript
"verb": {
        "id": "http://activitystrea.ms/schema/1.0/access",
        "display": {
            "en" : "accessed"
        }
    },
```

### Object
Common entity identifier: Object.*

#### Entity Example:
This object, a device, represents the access point being accessed and is uniquely identified by it's MAC address.

#### Example:
``` javascript
"object": {
  "objectType": "Activity",
  "id": "https://jisc.ac.uk/wifi", //not sure about this
  "definition": {
    "type": "http://activitystrea.ms/schema/1.0/device",
    "name": {
      "en": "University of Jisc wifi access point"
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/macAddress": "2A3DDE45B7B9"
    }
  }
}
```

### Context
Common entity identifier: Context.*

#### Context Example:
This context is an object that represents the client device that accessed the access point at a given time and is uniquely identified by it's MAC address.


``` javascript
"context": {
  "extensions": {
	"http://xapi.jisc.ac.uk/macAddress": "2A3DDE45B7B9",
    "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
    "http://xapi.jisc.ac.uk/recipeVersion" : "wifi_access_recipe0.1"
  }
}
```

