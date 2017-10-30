# tracking app. Record an activity against a target 


## Purpose
This recipe defines the structure and terms to record the experience of using a tracking app. 


## Recording an activity

### Verb

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/created",
        "display": {
            "en": "created"
        }
    },
```

### Object

The object should be the target.

### Example

``` javascript
"object": {
  "objectType": "Activity",
  "id": "https://jisc.ac.uk/studygoal/target?id=100",
  "definition": {
    "type": "https://xapi.jisc.ac.uk/target",
    "name": {
      "en": "Target"
    },
    "extensions": {
    	"http://xapi.jisc.ac.uk/target_value" : "20"
    }
  }
}
