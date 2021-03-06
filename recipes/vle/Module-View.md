# vle_resource_viewed Statement template

Based on generic Statement template: [Viewed](/generic/view.md)

[Statement Template Changes](/version_changes.md#vle-resource-viewed)

## Purpose
This template defines the structure and terms to record the experience of viewing a vle resource such as a Moodle Module or Blackboard building block (eg a page as identified by its url).

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

The Actor entity describes the individual that is viewing a vle resource.

### Example:

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "jsmith12",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb, [viewed](/vocabulary.md#verb) denotes the action of the user's browser or app requesting the resource that the user wishes to view.

### Example:

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/viewed",
        "display": {
            "en": "viewed"
        }
    },
```
### Object
Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

For this Statement the Object needs to identify what was viewed. A list of valid values for the object.definition.type can be found on the [vocabularies page](/vocabulary.md#activity-types).

Some statements may make use of subTypes of Activity Types. These sub-types are not defined by the Jisc profile spec, but for guidance examples can be found on the [vocabularies page](/vocabulary.md#activity-types) within the description of each valid activity type. It is the responsibility of the plugin to define the subType but the vendors do not own the IRI since these subTypes use a Jisc-controlled namespace that relates to the vendor, vendor product, or institution which de facto defines the sub-type.


### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://moodle.data.alpha.jisc.ac.uk/mod/page/view.php?id=9" 	 	
	"definition": {
		"type": "http://xapi.jisc.ac.uk/vle/page",			
		"name": { "en": "Sample page" },			   
	 }
	 "extensions": {
     		 "http://xapi.jisc.ac.uk/subType": "http://moodle.xapi.jisc.ac.uk/page"
	 }
    }
}
```

### Context

Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page. In this Statement, the courseArea extension is required. See the [vocabularies](/vocabulary.md#coursearea) page for more information.

### Example:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
	
      	"http://xapi.jisc.ac.uk/courseArea": {
			"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
			"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0"
		},

    "http://xapi.jisc.ac.uk/statementCat": "VLE",				
	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
	"http://xapi.jisc.ac.uk/version" : "1.0.1"
			}
        }
```

### Timestamp

In viewed statements the timestamp property must be set to the date and time at which the user viewed the resource.

#### Example:

 "timestamp": "2016-02-05T10:00:00.000Z"


### Complete VLE Specific Examples
[Moodle Example](/vle/moodle/moduleview.js)

[Blackboard Example](/vle/blackboard/course_content_access.json)
