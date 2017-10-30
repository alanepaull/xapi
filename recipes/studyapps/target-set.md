#tracking app set a target statement

## Purpose
This statement defines the structure and terms to record the experience of setting a target in the tracking app. 

## Setting a target 

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
      "http://xapi.jisc.ac.uk/uddModInstanceID" : "2016.sem1.psy101"
      "http://xapi.jisc.ac.uk/target_name" : "Reading for exams "
      "http://xapi.jisc.ac.uk/target_catergory" : "Reading"
      "http://xapi.jisc.ac.uk/target_value" : "120"
      "http://xapi.jisc.ac.uk/target_time_period" : "Week"	
    }
  }
}
