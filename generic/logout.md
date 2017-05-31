# Generic logged_out statement template

## Purpose
This generic statement template describes a user logging out of a VLE.

The entities and properties described here represent a typical statement template. Further properties or constraints could be defined to create a login statement template for a more specific purpose.

Natural language example of a typical logout statement: "John Smith logged out of his university Moodle VLE using his mobile phone."


## Statement template and JSON examples in Jisc Profile:

- [VLE Logout](/recipes/vle/logout.md)
- [Blackboard VLE Login](/vle/blackboard/loggedout.json)
- [Moodle VLE Login](/vle/moodle/logout.js)

### Actor
The actor entity is used to identify the individual that is logging out. It uses the Jisc profile common entity [ActorA](/common_structures.md#actora).

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
  "objectType": "Agent",
  "name": "John Smith",
  "account": {
    "name": "jsmith12",
    "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
  }
}
```

### Verb
The verb used in log out statements is  [logged out](/vocabulary.md#verbs) describes the action of logging out of a platform.  It describes the action of logging into a platform. It uses the Jisc common entity [VerbA](../common_structures.md#verba). 


####  Entity properties:


<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. For logging out statements the iri https://brindlewaye.com/xAPITerms/verbs/loggedout is used</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag.  For logging out statement "Logged out of".</td>
	</tr>
</table>


#### Example:

``` javascript
"verb": {
  "id": "https://brindlewaye.com/xAPITerms/verbs/loggedout",
  "display": {
    "en" : "logged out"
  }
}
```

### Object
The object for logout statements identifies what is being logged out of. It uses the Jisc Profile common entity [ObjectA](../common_structures.md#objecta),

#### Entity properties:


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

### Example
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


### Context
Context can be used to describe any surrounding circumstances to the logout, including for example the device used to login. If the device supports it, session Ids and ip-addresses can be recorded. Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page. 

#### Entity properties:


<table>
<tr><th>Property</th><th>Description</th></tr>
	<tr><td>context.platform [1]</td>
	<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard"</td></tr>
	<tr><td>context.extensions.version [0..1]
		 context.extension.sessionId [0..1]
		 context.extension.ip-address [1]
		 </td>
		<td>Four extensions are provided for, with IRIs as defined on the <a href="vocabulary.md#41-context-extensions">vocabularies page</a>.
  	  The <b>sessionID</b> extension is the VLE session ID, or a suitably hashed version of it. A value should be provided if this information is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended, and identifies the version of the Jisc xAPI profile found on the ReadMe page. <br/>
		</td></tr></table>

### Example:

``` javascript
"context": {
  "platform": "Moodle",
  "extensions": {
    "http://xapi.jisc.ac.uk/sessionId": "L5t1W93PED",
    "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48",
    "http://xapi.jisc.ac.uk/version" : "1.0"
  }
}
```

