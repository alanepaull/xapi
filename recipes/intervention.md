---
layout: home
---

#intervention Recipe
Revision: 0.1 

## Purpose
This activity records a service creating an intervention for a person.

## Draft Notes
In this draft the actor is the service, the object is the person the intervention is sent to, and the context describes the intervention activity. 

An alternative draft could cast the agent as the person the intervention is sent to, the object describes the intervention activity and the context the system? But the person is passive in this recipe?

## Definition
### Actor
 

The actor is the system that sends the intervention.

List of valid systems in the jisc profile: //do we need a list of systems in the profile?

* https://www.unicon.net/opensource/student-success-plan


``` Javascript
"actor": {
	 "objectType : Agent" ,
     "name": "Student Success Plan",
     "openid" : " " // I take it that we can't use account object because there is no account, Possible options are openid , mbox_sha1sum and mbox
```

### Verb

//need to mint a verb?

The verb, intervene describes an intervention by the actor on the object.

``` javascript
"verb": {
        "id": "http://xapi.jisc.ac.uk/authorize",
        "display": {
            "en": "intervene"
        }
    },
```


### Object

In this case, object is the person that has been sent an intervention 

``` Javascript
{
    "object": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Context

The Context describes the intervention itself


``` javascript
"context": {
	"contextActivities":{
            "grouping":[
                {
                    "objectType":"Activity",
                    "id":"", // ?
                    "definition":{
                        "type":"http://xapi.jisc.ac.uk/intervention",
                        "description":{
                            "en":" //?
                        }
                    }
                }
            ]
        }
```


