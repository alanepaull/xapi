# mobile_app content viewed recipe
Revision: 1.3

## Purpose
This recipe defines the structure and terms to record the experience of viewing a tracking app. 

Basic viewing is dealt with in mobile-app.

The basic actions to consider are:

* Set a target

* Record an activity against a target

* Reach a target

* Post an update  (this is unrelated to targets).

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

The object should be the target.  What should the object type defintion be though?   

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

The object should be the target.  What should the object type defintion be though?   

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


### Verb

``` javascript
"verb": {
        "id": "http://adlnet.gov/expapi/verbs/completed",
        "display": {
            "en": "created"
        }
    },
```

### Object

``` javascript
"object": {
  "objectType": "Activity",
  "id": "https://jisc.ac.uk/studygoal/target?id=100",
  "definition": {
    "type": "https://xapi.jisc.ac.uk/target",
    "name": {
      "en": "Target"
    }
  }
}


