# read-list-viewed statement template

Based on generic template statement: [Viewed](/generic/view.md)

[Statement Template Changes](/version_changes.md#library-reading-list-viewed)

## Purpose
This template defines the structure and terms to record the experience of viewing a reading list

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

The actor entity describes the individual that is viewing the reading list.

### Example:

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "account": {
            "name": "stu1",
            "homePage": "https://library.alpha.jisc.ac.uk/"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb,[viewed](/vocabulary.md#verbs) denotes the action of the user's browser or app requesting the reading list.

### Example:

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/viewed",
        "display": {
            "en": "viewed"
        }
    },
```

### Context
Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contexta) page.
The courseArea is required and gives information reguarding the module the reading list belongs to. See the [vocabularies](../vocabulary.md#coursearea-properties) page for more information

### Example:

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

### Object

Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

For this recipe the object needs to identify what was viewed. A list of valid values  for the object definition type can be found on the[vocabularies page](/vocabulary.md#Object.definition.extension)

### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "<iri of reading list>"   	 	
	"definition": {
		"type": "http://xapi.jisc.ac.uk/reading-list",			
		"name": { "en": "Sample page" },			   
	 }
	 "extensions": {
     		 "http://xapi.jisc.ac.uk/subType": "<subtype of reading list>"
	 }
    }
}
```


