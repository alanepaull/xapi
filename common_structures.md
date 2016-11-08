---
layout: home
---

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
		<td>actor.objectType [1]</td>
		<td>
		Must have the value "Agent". Actors of type "Group" are not supported in the Jisc profile.
		</td>
	</tr>
	<tr>
		<td>actor.name [0..1]</td>
		<td>Full name of user.</td>
	</tr>
	<tr>
		<td>	
			actor.account [1] <br />
		    actor.account.name [1] <br />
		    actor.account.homepage [1]
</td>
		<td>A JSON Object with <b>account.name</b> giving the login id for the subject of the statement and <b>account.homepage</b> giving the URL of the home page of the application for which the login id applies.</td>
	</tr>
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

The Verb structure indicates the action which the statement expresses. The verbs used in the Jisc profile are listed on the [vocabularies](vocabulary.html#verb) page.

<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. Valid IRIs depend on the recipe and are given on the relevant recipe page.</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag.  
		The verb.display is "recommended" in the xAPI v1.0.1 specification but is not likely to be of use within the Jisc Learning Analytics architecture.</td>
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
Depending on the recipe, different patterns describe the context of a statement.

### ContextA
Common entity identifier: ContextA

This pattern is used across many recipes in the Jisc profile, but there may be additional data elements required for some recipes.

<table>
	<tr><th>Property</th><th>Description</th></tr>
	
	<tr>
		<td>context.platform [1]</td>
		<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard"</td>
	</tr>
	<tr>
		<td>context.extensions.recipeVersion [0..1]<br/>
		 context.extension.sessionId [0..1]<br/>
		 context.extension.ip-address [1]
		 </td>
		<td>
		Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.html#41-context-extensions">vocabularies page</a>.<br/>
  	  The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>recipeVersion</b> extension is recommended, and identifies the recipe (and its version) which was followed to create the xAPI statement. <br/>
	The <b>courseArea</b> identifies Umbrella course/parent area by its home page URI. More information can be found on the <a href="vocabulary.html#umbrella-course-area">vocabularies page</a>.
		</td>
		</tr>
</table>

#### Example:
``` javascript
"context": {
  "platform": "Moodle",
  "extensions": {
    "http://xapi.jisc.ac.uk/sessionId": "32456891",
    "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
    "http://xapi.jisc.ac.uk/recipeVersion" : "vle_logged_inV1.3"
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
			context.extensions.recipeVersion [1]
</td>
		<td>Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.html#41-context-extensions">vocabularies page</a>.<br/>
    The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if it is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>recipeVersion</b> extension is recommended, and identifies the recipe (and its version) which was followed to create the xAPI statement.
	<br/>
    The <b>courseArea</b> extension is recommended, and identifies umbrella course/parent area by its home page URI. More information can be found on the <a href="vocabulary.html#umbrella-course-area">vocabularies page</a>.</td>
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
                "id": http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
				},
			
 			"http://xapi.jisc.ac.uk/sessionId":"32456891",
            "http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
			"http://xapi.jisc.ac.uk/recipeVersion" : "vle_assignment_submittedV1.3"
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
			context.extensions.recipeVersion [1]
</td>
		<td>Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.html#41-context-extensions">vocabularies page</a>.<br/>
    The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if it is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>recipeVersion</b> extension is recommended, and identifies the recipe (and its version) which was followed to create the xAPI statement.
	<br/>
    The <b>courseArea</b> extension is recommended, and identifies umbrella course/parent area by its home page URI. More information can be found on the <a href="vocabulary.html#umbrella-course-area">vocabularies page</a>.</td>
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
	object.definition.extensions.http://xapi.jisc.ac.uk/uddModInstanceID [0..1]</td>
		<td>A JSON object comprising both standard xAPI attributes and the Jisc profile 'subType' and 'uddModInstanceID' extensions.<br/>
    The <b>type</b> indicates the type of the object of the statement. It is required and valid values are listed on the <a href="vocabulary.html#31-activity-types">vocabulary page</a>.</br>
    The <b>name</b> is optional.</br>
    The <b>subType</b> extension may be used to indicate the sub-type of this activity, if applicable for the recipe being used to create the statement. This qualifies the object.objectType, and is described on the [vocabularies](vocabulary.html#32-object-definition-extensions) page.<br />
    The <b>uddModInstanceID</b> extension records the module instance with which the learning activity is associated. See the <a href="vocabulary.html#31-activity-types">vocabulary page</a> for more details.</td>
	</tr>
	
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
      "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms",
      "http://xapi.jisc.ac.uk/uddModInstanceID" : "2016.sem1.psy101"
    }
  }
}
```

### ObjectB
Common entity identifier: ObjectB

This object pattern describes an activity that has been completed. Examples of valid object.definition vocabulary Activity object Types are listed on the [vocabularies](vocabulary.html) page.


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
		<td>
			object.instructor [0..1] <br />
			object.instructor.objectType [1] <br />
			object.instructor.name [0..1] <br />
		    object.instructor.account.name [1] <br />
		    object.instructor.account.homepage [1]
</td>
		<td>A JSON Object. <b>object.instructor.objectType</b> typically has "Agent" as a value. <br /><b>object.instructor.name</b> gives the name of the role, which is typically "instructor". <br /> <b>account.name</b> gives the login id for the instructor. <br /> <b>account.homepage</b> gives the URL of the home page of the application for which the login id applies.</td>
	</tr>
	<tr>
		<td>object.definition 
			object.definition.type [1]<br />
			object.definition.name [0..1]<br />
			object.definition.description [0..1]<br />
			object.definition.extensions.http://xapi.jisc.ac.uk/dueDate [0..1]
</td>
		<td>The <b>object.definition.type</b> indicates the type of the object of the statement. Valid values are listed on the <a href="vocabulary.html#31-activity-types">vocabulary page</a>.<br />
		The <b>object.definition.name</b> holds a human readable name of the object type.</br>
		The <b>description</b> holds a description of the object type.</br>
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
			"type":"http://adlnet.gov/expapi/activities/module",
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

The object pattern defines an activity that has been completed. [Examples of valid object.definition Activity object Types can be found in the vocabulary](../vocabulary.html#30-object).

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
		<td>The <b>type</b> indicates the type of the object of the statement. It is required and valid values are listed on the <a href="vocabulary.html#31-activity-types">vocabulary</a> page.</br>
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

### ResultB
Common entity identifier: ResultB

This result pattern describes completion and is usually optional. This result entity can include scaled, raw, min and max score, success, and response (the instructor's feedback). See [result](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.html#result). See the [vocabulary](../vocabulary.html) page for a definition of the 'http://xapi.jisc.ac.uk/grade' extension.

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr>
		<td>result.score.raw [0..1]</td>
		<td>Decimal number</td>
	</tr>
		<tr>
		<td>result.extensions.http://xapi.jisc.ac.uk/grade [0..1]</td>
		<td>A non-numerical assessment result. Data type is string (256)</td>
	</tr>
</table>

#### Example:
``` javascript
 "result":{
        "completion":true
    }
```



