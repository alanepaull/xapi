# Generic login generic statement template

## Purpose
This generic statement template describes a user logging in to something. Use this template to create a specific login statement template, for example for a student logging in to a VLE.

The entities and properties described here represent a typical statement template. Further properties or constraints could be defined to create a login statement template for a more specific purpose.

Natural language example of a typical login statement: "John Smith logged in to his university Moodle VLE using his mobile phone."

## Statement template and JSON examples in Jisc Profile:

- [VLE Login](/recipes/vle/login.md)
- [Blackboard VLE Login](/vle/blackboard/loggedin.json)
- [Moodle VLE Login](/vle/moodle/login.js)

### Actor Entity
The actor entity is used to identify the individual that is logging in. It uses the Jisc profile common entity [ActorA](/common_structures.md#actora).

#### Actor Entity properties:

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
<td>A JSON Object with <b>account.name</b> giving a system login id for the Actor and <b>account.homepage</b> giving the URL of the home page of the application to which the login id applies.</td></tr>
</table>

### Actor Example:

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

### Verb Entity
The verb used in login statements is [logged in](../vocabulary.md#logged-in). It describes the action of logging into a platform. It uses the Jisc common entity [VerbA](../common_structures.md#verba). 

#### Verb Entity properties:
<table>
	<tr><th>Property</th><th>Description</th></tr>
	<tr>
		<td>verb.id [1]</td>
		<td>An IRI that identifies the Verb. For logged in statements the Jisc profile uses https://brindlewaye.com/xAPITerms/verbs/loggedin verb id</td>
	</tr>
	<tr>
		<td>verb.display [1]</td>
		<td>A human readable representation of Verb. It takes a RFC 5646 Language Tag. For logged in statements use "logged in"</td>
	</tr>
</table>

#### Verb Example
``` javascript
"verb": {
  "id": "https://brindlewaye.com/xAPITerms/verbs/loggedin",
  "display": {
    "en" : "logged in"
  }
}
```

### Object Entity
The object for Login statements identifies what is being logged in to. It uses the Jisc Profile common entity [ObjectA](../common_structures.md#objecta),

#### Object Entity properties:
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
	object.definition.extensions.http://xapi.jisc.ac.uk/subType [0..1]<br /></td>
		<td>A JSON object comprising both standard xAPI properties and the Jisc profile 'subType' extension.<br/>
    The <b>type</b> classifies generally what is being logged into, for example an application or a platform. Valid values are listed on the <a href="../vocabulary.md#31-activity-types">vocabulary page</a>.<br/>
    The <b>name</b> is optional.<br/>
    The <b>subType</b> extension may be used to further qualify the object.objectType, and is described on the [vocabularies](vocabulary.md#32-object-definition-extensions) page.<br /></tr>
	
</table>

#### Object Example:
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

### Context Entity
Context can be used to describe any surrounding circumstances to the login, including for example the device used to login. If the device supports it, session Ids and ip-addresses can be recorded. Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page. 

#### Context Entity properties:
<table>
<tr><th>Property</th><th>Description</th></tr>
	<tr><td>context.platform [1]</td>
	<td>The platform used in the experience of this learning activity. The value used should not change between platform upgrades and version changes and should typically be a concise name by which the application is commonly known, for example "Moodle" or "Blackboard"</td></tr>
	<tr><td>context.extensions.version [0..1]
		 context.extension.sessionId [0..1]
		 context.extension.ip-address [1]
		 </td>
		<td>Four extensions are provided for, with IRIs as defined on the <a href="../vocabulary.md#41-context-extensions">vocabularies page</a>.
  	  The <b>sessionID</b> extension is the identifier of the user's session, or a suitably hashed version of it. A value should be provided if this information is available.<br/>
    The <b>ip-address</b> is used to identify the client's IP address. An IPv4 address is recommended.<br/>
    The <b>version</b> extension is recommended and identifies the xAPI Profile version. <br/></td></tr></table>
			
#### Context Entity Example:
``` javascript
"context": {
  "platform": "Moodle",
  "extensions": {
    "http://xapi.jisc.ac.uk/sessionId": "L5t1W93PED",
    "http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
    "http://xapi.jisc.ac.uk/version" : "1.0"
  }
}
```



