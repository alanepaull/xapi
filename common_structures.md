# Jisc Learning Analytics Common Structures
The following sections describe common patterns used across several of the recipes.
Wherever a recipe refers to a "common entity identifier", the example given in the recipe follows one of the patterns given on this page.

## ActorA
Common entity identifier:  ActorA

This entity is required across all recipes in the Jisc profile.

The actor entity describes the individual that is the subject of the statement.

<table>
<tr><th>Property</th><th>Description</th></tr>
<tr>
<td>actor.objectType [1]</td><td>Must have the value "Agent". Actors of type "Group" are not supported in the Jisc profile.</td>
</tr>
<tr>
<td>actor.name [0..1]</td><td>Full name of user.</td>
</tr>
<tr>
<td>	
actor.account [1] <br/>
actor.account.name [1] <br/>
actor.account.homepage [1] <br/>
</td>
<td>A JSON Object with <b>account.name</b> giving the login id for the subject of the statement and <b>account.homepage</b> giving the URL of the home page of the application for which the login id applies.</td></tr>
</table>

### Example
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

## VerbA
Common entity identifier: VerbA

This entity is required across all recipes in the Jisc profile.

The Verb structure indicates the action which the statement expresses. The verbs used in the Jisc profile are listed on the [vocabularies](vocabulary.md#verb) page.

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. Valid IRIs depend on the recipe and are given on the relevant recipe page.</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag. </td>
	</tr>
</table>


### Example
``` javascript
"verb": {
  "id": "https://brindlewaye.com/xAPITerms/verbs/loggedin",
  "display": {
    "en" : "logged in to"
  }
}
```

## Context
Depending on the recipe, different patterns describe the circumstances that form the setting of the statement, so that it can be better understood.

### ContextA
Common entity identifier: ContextA

This pattern is used across many recipes in the Jisc profile, but there may be additional data elements required for some recipes.

<table>
<tr><th>Property</th><th>Description</th></tr>
	<tr><td>context.platform [1]</td>
	<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard"</td></tr>
	<tr><td>context.extensions.version [0..1]</td>
		 context.extension.sessionId [0..1]</td>
		 context.extension.ip-address [1]</td>
		 context.extension.courseArea [0..1]</td>
		 </td>
		<td>Three extensions are provided for, with IRIs as defined on the <a href="vocabulary.md#extensions">vocabularies page</a>.
  	  The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI profile found on the ReadMe page. <br/>
	The <b>courseArea</b> identifies Umbrella course/parent area by its home page URI and / or its identifier. More information can be found on the <a href="vocabulary.md#course-area">vocabularies page</a>.
	</table>

#### Example:
``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
	
			"http://xapi.jisc.ac.uk/courseArea": {
				"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
				"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
				"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
		},
					
		"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
		"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
		"http://xapi.jisc.ac.uk/version" : "1.0"
			}
        }
``` 
### ContextB
Common entity identifier: ContextB

ContextB pattern is similar to ContextA, but with the addition of a contextActivities property with a ‘grouping’ property. This allows statements to be associated to the activity described in the object entities as part of a larger whole.

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>context.contextActivities [0..1]<br />
		context.contextActivities.grouping [1]
		</td>
		<td>An optional property that holds a mandatory ‘grouping’ property. It allows statements to be associated with the object entity's activity as part of a larger whole. The example shows a course within the VLE. The 'grouping' property has an <a href="#objecta">ObjectA</a> as its value.</td>
	</tr>
	<tr>
		<td>context.platform [1]</td>
		<td>The platform used in the experience of this learning activity. This is required. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard"</td>
	</tr>
	<tr>
		<td> context.extensions.courseArea [0..1]<br />
			context.extensions.sessionId [0..1]<br />
			context.extensions.ip-address [1]<br />
			context.extensions.version [0..1]
</td>
	    <td>Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.md#extensions">vocabularies page</a>.<br/>
    The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if it is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI profile found on the ReadMe page.
	<br/>
    The <b>courseArea</b> extension is recommended, and identifies umbrella course/parent area by its home page URI. More information can be found on the <a href="vocabulary.md#course-area">vocabularies page</a>.</td>
		</tr>
</table>

#### Example:
``` javascript
"context": {
	"contextActivities":{
            "grouping":[
                {
                    "objectType":"Activity",
                    "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
                    "definition":{
                        "type":"http://xapi.jisc.ac.uk/courseArea",
                        "name":{
                            "en":"xAPI Basics"
                        },
                        "description":{
                            "en":"xAPI Basics course for Learning Analytics enthusiasts"
                        }
                    }
                }
            ]
        },
        
        "platform": "Moodle",
        "extensions": {
		
			"http://xapi.jisc.ac.uk/courseArea": {
				"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
				"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
				"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
			},
			
 		"http://xapi.jisc.ac.uk/sessionId":"32456891",
        "http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
		"http://xapi.jisc.ac.uk/version" : "1.0"
			}
		}
```

### ContextC
Common entity identifier: ContextC

ContextC pattern is similar to ContextB, but is designed to be used with systems that are not directly controlled by the learner. 

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>context.contextActivities [0..1]<br />
		context.contextActivities.grouping [1]
		</td>
		<td>An optional property that holds a mandatory ‘grouping’ property. It allows statements to be associated with the object entity's activity as part of a larger whole. The example shows a course within the VLE. The 'grouping' property has an <a href="#objecta">ObjectA</a> as its value.</td>
	</tr>
	<tr>
		<td>context.platform [1]</td>
		<td>The platform used to record something about the learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Sentry"</td>
	</tr>
	<tr>
		<td> context.extensions.courseArea [0..1]<br />
		context.extensions.version [1]<br />
		context.extension.sessionId [0..1]<br />
		context.extension.ip-address [1] <br />
</td>
		<td>Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.md#41-context-extensions">vocabularies page</a>.<br/>
    The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if it is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI profile found on the ReadMe page.
	<br/>
    The <b>courseArea</b> extension is recommended, and identifies umbrella course/parent area by its home page URI. More information can be found on the <a href="vocabulary.md#course-area">vocabularies page</a>.</td>
		</tr>
</table>

### ContextD

<table>
<tr><th>Property</th><th>Description</th></tr>
<tr>
<td>context.instructor [0..1]<br/>
context.instructor.objectType [1]<br/>
context.instructor.account.homepage [1] <br/>
context.instructor.account.name [1] <br/>
</td>
<td>
A JSON Object. object.instructor.objectType has "Agent" as a value. account.name gives the login id for the instructor. <br/>
and context.account.homepage gives the URL of the home page of the application for which the login id applies.
</td></tr><tr>
<td>
context.extensions.version [0.1]
context.extensions.https://xapi.jisc.ac.uk/devicelocation [0.1]
context.extensions.https://xapi.jisc.ac.uk/courseArea [0.1]
</td>
<td>
The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI profile found on the ReadMe page.<br/>
devicelocation is an optional geojson object with  geolocation details of the device used to attend the event.<br/>	The <b>courseArea</b> identifies Umbrella course/parent area by its home page URI and / or its identifier. More information can be found on the <a href="vocabulary.md#course-area">vocabularies page</a>.

</td>
</tr>
</table>


## Object
Depending on the recipe, different patterns apply to express the object of a statement.

### ObjectA
Common entity identifier: ObjectA

This object pattern describes the core attributes of Object as used in the Jisc profile.

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for the object of the xAPI statement. This must be unique (within a given platform) across all object types.</td>
	</tr>
		<tr>
		<td>object.definition.type [1]<br />
	object.definition.name [0..1]<br />
	object.definition.extensions.http://xapi.jisc.ac.uk/subType [0..1]<br />
		<td>A JSON object comprising both standard xAPI attributes and the Jisc profile 'subType' and 'uddModInstanceID' extensions.<br/>
    The <b>type</b> indicates the type of the object of the statement. It is required and valid values are listed on the <a href="vocabulary.md#31-activity-types">vocabulary page</a>.<br/>
    The <b>name</b> is optional.<br/>
    The <b>subType</b> extension may be used to indicate the sub-type of this activity, if applicable for the recipe being used to create the statement. This qualifies the object.objectType, and is described on the [vocabularies](vocabulary.md#32-object-definition-extensions) page.<br />

	
</table>

#### Example:
``` javascript
"object": {
  "objectType": "Activity",
  "id": "https://courses.alpha.jisc.ac.uk/moodle",
  "definition": {
    "type": "http://activitystrea.ms/schema/1.0/application",
    "name": {
      "en": "University of Jisc VLE"
    },
    "extensions": {
      "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
    }
  }
}
```

### ObjectB
Common entity identifier: ObjectB

This object pattern describes an activity that has been completed. Examples of valid object.definition vocabulary Activity object Types are listed on the [vocabularies](vocabulary.md) page.


<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for a single unique Activity</td>
	</tr>
	<tr>
			<td>object.definition<br/>
			object.definition.type [1]<br />
			object.definition.name [0..1]<br />
			object.definition.extensions.http://xapi.jisc.ac.uk/dueDate [0..1]
</td>
		<td>The <b>object.definition.type</b> indicates the type of the object of the statement. Valid values are listed on the <a href="vocabulary.md#31-activity-types">vocabulary page</a>.<br />
		The <b>object.definition.name</b> holds a human readable name of the object type.<br/>
 <b>"http://xapi.jisc.ac.uk/dueDate"</b> is a ISO 8601 date time that indicates when an assignment is due</td>
		</td>
	</tr>
</table>

#### Example:
``` javascript
"object":{

		"objectType":"Activity",
		"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
		"definition":{
			"type":"http://adlnet.gov/expapi/activities/assesment",
			"name":{
				"en":"Course Assignment"
			},
			"description":{
				"en":"Course Assignment description"
				}
			},
			
		    "extensions":{
				"http://xapi.jisc.ac.uk/dueDate": "2016-02-05T17:59:45.000Z"
			}
			
		}
```

### ObjectC
Common entity identifier: ObjectC

The object pattern defines an activity that has been completed. [Examples of valid object.definition Activity object Types can be found in the vocabulary](../vocabulary.md#30-object).

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for a single unique learning event.</td>
	</tr>
	<tr>
		<td>object.definition [1]<br/>
		object.definition.type [1]<br/>
		object.definition.extension.http://id.tincanapi.com/extension/datetime [1]<br/>
		object.definition.extension.http://id.tincanapi.com/extension/duration [0..1]</td>
		<td>The <b>type</b> indicates the type of the object of the statement. It is required and valid values are listed on the <a href="vocabulary.md#31-activity-types">vocabulary</a> page.</br>
				The <b>name</b> holds the name of the learning activity.</br>
		The <b>description</b> describes the learning activity.</br>
<b>"http://id.tincanapi.com/extension/datetime"</b> is an extension that holds a ISO 8601 date time that indicates when the learning event started.<br /><b>"http://id.tincanapi.com/extension/duration"</b> represents the length of time the event is scheduled to take, expressed as a string formatted as an ISO8601 duration. Note that ISO8601 duration allows representations to extend beyond their carry over points. e.g. one and a half hours can be represented as either PT1H30M or PT90M.</td>
	</tr>
</table>

Example:

``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://www.poppleton.ac.uk/psy101/lecture1",
		"definition":{
			"type":"http://activitystrea.ms/schema/1.0/event",
			"name":{
				"en":"Lecture"
			},
			"description":{
				"en":"The first lecture of psychology 101"
				}
			},
			
		    "extensions":{
				"http://id.tincanapi.com/extension/datetime": "2016-02-05T10:00:00.000Z",
				"http://id.tincanapi.com/extension/duration": "PT1H30M"
			}
			
		}
		
```

### ObjectD

The object pattern defines an event that has been attended.

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for a single unique learning event.</td>
	</tr>
	<tr>
	   <td>object.definition [1]<br>
	       object.definition.type [1]<br/>
	       object.definition.name [0.1]<br/>
	       object.definition.description [0.1]<br/>
	       object.definition.extensions.http://xapi.jisc.ac.uk/subType [0.1]<br/>
	       object.definition.extensions.http://xapi.jisc.ac.uk/event_type_id [0.1]<br/>
	       object.definition.extensions.http://xapi.jisc.ac.uk/event_type_description [0.1]<br/>
	       object.definition.extensions.http://xapi.jisc.ac.uk/event_max_count [0.1]<br/>
	       object.definition.extensions.http://xapi.jisc.ac.uk/event_mandatory [0.1]<br/>
	       object.definition.extensions.http://xapi.jisc.ac.uk/starttime [0.1]<br/>
	       object.definition.extensions.http://xapi.jisc.ac.uk/endtime [0.1]<br/>
	   </td>
	   <td>The <b>type</b> indicates the type of the object of the statement. It is required and must contain the value "http://xapi.jisc.ac.uk/event_timetabled" (see <a href="vocabulary.md#31-activity-types">vocabulary</a> page).<br/>
	   The <b>name</b> holds the name of the event.<br/>
	   The <b>description</b> describes the learning activity.<br/>
	   The <b>subType</b> may be used to qualify what kind of timetabled event occurred using an IRI given on the <a href="vocabulary.md#31-activity-types">vocabulary</a> page. Permitted values are: "http://xapi.jisc.ac.uk/lecture" or "	http://id.tincanapi.com/activitytype/tutor-session".<br/>
	   The <a href ="/vocabulary.md#event-type-id">event_type_id</a> requires an identifier for the type of even<br/> <a href="/vocabulary.md#event-type-description">event_type_description</a> is a description of the event type<br/><a href="/vocabulary.md#event-max-count">event_max_count</a><br/> is the maximum number of people that could have attended the event. <a href="/vocabulary.md#event-mandatory">event_mandatory</a>  states if the event was optional or not <br/> <b>object.extensions.http://xapi.jisc.ac.uk/starttime</b> is the planned start time. Uses datetimes for planned end of event. <br/><b>object.extensions.http://xapi.jisc.ac.uk/endtime</b> The planned end time of event. Uses datetimes for planned end time of event.  <br/>
	    </td>  
		
	</tr>
 </table>

## Result
In the Jisc profile, the use of the result entity and any of its properties is optional.

### ResultA
Common entity identifier: ResultA

This result pattern describes the completion of a learning activity and is optional.

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr>
		<td>result.completion [0..1]</td>
		<td>"true". Indicates that the Activity was completed</td>
	</tr>
</table>

#### Example:
``` javascript
 "result":{
        "completion":true
    }
```

## ResultB
Common entity identifier: ResultB
This result pattern describes completion and is usually optional. It can include scaled, raw, min and max score, success, and response (the instructor's feedback). See [score](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.md#Score). See the [vocabulary](https://github.com/jiscdev/xapi/blob/vocabulary.md) page for a definition of the 'http://xapi.jisc.ac.uk/grade' extension.

<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Data type</th></tr>
	<tr>
		<td>result.score.scaled [0..1]</td>
		<td>The score related to the experience as modified by scaling and/or normalization</td>
<td>decimal number between -1 and 1, inclusive.</td>
	</tr>
	<tr>
		<td>result.score.raw [0..1]</td>
		<td>Unmodified score</td>
<td>decimal number between min and max (if present, otherwise unrestricted), inclusive</td>
	</tr>
	<tr>
		<td>result.score.min [0..1]</td>
		<td>The lowest possible score</td>
<td>decimal number less than max (if present)</td>
	</tr>
	<tr>
		<td>result.score.max [0..1]</td>
		<td>The highest possible score</td>
		<td>decimal number greater than min (if present)</td>
	</tr>
	<tr>
		<td>result.success [0..1]</td>
		<td>Indicates whether or not the attempt was successful.</td>
		<td>true or false</td>
	</tr>
	<tr>
		<td>result.response [0..1]</td>
		<td>Instructor's or automatic feedback</td>
		<td>string (256)</td>
	</tr>
	<tr>
		<td>result.extensions.http://xapi.jisc.ac.uk/grade [0..1]</td>
		<td>Non-numerical assessment result</td>
		<td>string (256)</td>
	</tr>
</table>

## Example:

```
"result": {
        "score": {
            "scaled": 0.25,
            "raw": 25,
            "min": 0,
            "max": 100
        },
		
        "success": false,
        "completion": true,
        "response": "The cow jumped over the moon."
         }

````

For grade, leave out min and max, and insert the following:
````
        "extensions": { 
             "http://xapi.jisc.ac.uk/grade": "5 Stars"
        }
````
### ResultC
Common entity identifier: ResultC

This pattern describes the result and if the actor was on time to the event, if they were late and what category a late

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr><td>result.completion [1]</td><td>When set to "true", result.completion indicates that the learner attended the event. "false"indicates that the learner did not attend the event.</td>
	</tr>
	<tr><td>result.extension.http://xapi.jisc.ac.uk/attendance_late [0..1] <br/>
		    result.extension.http://xapi.jisc.ac.uk/attendance_category [0..1]
		</td>
		<td> <b>http://xapi.jisc.ac.uk/attendance_late</b> indicates whether the person was late.<br/> <b>http://xapi.jisc.ac.uk/attendance_category</b> indicates category for non-attendance or lateness.
</td>
	</tr>
</table>

### Example

``` javascript
 "result":{
        "completion":true,
		
		 "extensions":{
		  "http://xapi.jisc.ac.uk/attendance_late":"1",
		  "http://xapi.jisc.ac.uk/attendance_category":"1",
		 }
    }
```

### ResultD
Common entity identifier: ResultD

This pattern contains the content of the post.

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr><td>result.response [1]</td><td>Content of post or reply</td></tr>
</table>

### Example


``` javascript
 "result":{
        "response":"I have some good links on that subject, I will find them for you"
    }
``` 
