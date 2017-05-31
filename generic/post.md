# Post a discussion generic statement template

## Purpose
This template defines the structure and terms to record the experience of posting to a discussion forum.


Examples:

- [Forum Reply](../recipes/vle/forum-post.md)

### Actor
Common entity identifier:  [ActorA](/common_structures.md#actora)

The actor entity describes the individual that is posting a discussion.

#### Entity properties:

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
<td>A JSON Object with <b>account.name</b> giving a system login id for the subject of the statement and <b>account.homepage</b> giving the URL of the home page of the application for which the login id applies.</td></tr>
</table>

### Example:

``` Javascript
"actor": {
  "objectType": "<ObjectType set to Agent>",
  "name": "<Real Name: Example: John Smith>",
  "account": {
    "name": "<Account name: Example: jsmith12>",
    "homePage": "<URL of the home page for the application. Example: https://courses.alpha.jisc.ac.uk/moodle>"
  }
}
```

### Result
Common entity identifier: [ResultD](/common_structures.md#resultd)

This property contains the content of the post.

#### Entity properties:

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr><td>result.response [1]</td><td>Content of post or reply</td></tr>
</table>


#### Example:

``` javascript
 "result":{
        "response":"<Text posted: Example I have some good links on that subject, I will find them for you>"
    }
``` 

### Object
Common entity identifier: [ObjectA](/common_structures.md#objecta)

#### Entity Properties:
The object defines the forum that has been posted to,

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
    The <b>type</b> indicates the type of the object of the statement. It is required and valid values are listed on the <a href="vocabulary.md#31-activity-types">vocabulary page</a>.<br/>
    The <b>name</b> is optional.<br/>
    The <b>subType</b> extension may be used to indicate the sub-type of this activity, if applicable for the recipe being used to create the statement. This qualifies the object.objectType, and is described on the [vocabularies](vocabulary.md#32-object-definition-extensions) page.<br />
	</tr>
	
</table>

#### Entity Example:


 ``` javascript
"object": {
	"objectType": "<Objecttype: Activity",
	"id": "<id of forum or group being posted to. Example: http://moodle2.bolton.ac.uk/mod/forum/discuss.php?d=19474">	
	"definition": {
		"type": "<iri of the type of activity. In post statements: http://xapi.jisc.ac.uk/vle/forum-post>",			
		"name": { "en": "<name of sample post" },			   
	 }
	 "extensions": {
     		 "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
	 }
    }
}

```

#### Context

Common entity identifier: [ContextA](/common_structures.md#contexta)


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
		<td>context.extensions.courseArea [0..1]<br />
			context.extensions.sessionId [0..1]<br />
			context.extensions.ip-address [1]<br />
			context.extensions.ip-address [1]<br />
			context.extensions.version [1]
</td>
		<td>Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.md#41-context-extensions">vocabularies page</a>.<br/>
    The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if it is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI profile found on the ReadMe page.
	<br/>
    The <b>courseArea</b> extension is recommended, and identifies umbrella course/parent area by its home page URI. More information can be found on the <a href="vocabulary.md#umbrella-course-area">vocabularies page</a>.</td>
		</tr>
</table>

### Example:

``` javascript
"context": {
        "platform": "< Platform. Example: Moodle>",
        "extensions": {
	
      	"http://xapi.jisc.ac.uk/courseArea": {
	    "http://xapi.jisc.ac.uk/vle_mod_id": "<VLE_Mod_idLA101. Example: ",
            "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
		},
					
	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
	"http://xapi.jisc.ac.uk/version" : "1.0"
			}
        }
```
