#vle_resource_viewed recipe
Revision: 1.3

##Purpose
This recipe defines the structure and terms to record the experience of viewing a vle resource such as a Moodle Module or Blackboard building block (eg a page as identified by its url)

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](../common_structures.md#actora) page.

The actor entity describes the individual that is viewing a vle resource.

### Example:

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage: "jsmith12"https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](../common_structures.md#verba) page.

The Verb,[viewed](/vocabulary.md#verbs) denotes the action of the user's browser or app requesting the resource that the user wishes to view.

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
Common entity identifier: ContextA, as defined on the [common structures](../common_structures.md#contextc) page.

For this recipe the courseArea is required. See the [vocabularies](../vocabulary.md#42-coursearea-properties) page for more information

### Example:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
	
      	"http://xapi.jisc.ac.uk/courseArea": {
			"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
            "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
					},
					
		  	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
		  	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48"
			"http://xapi.jisc.ac.uk/recipeVersion" : "vle_resource_viewedV1.3"
			
			}
              
        }
```

### Object

Common entity identifier: ObjectA, as defined on the [common structures](../common_structures.md#objecta) page.

For this recipe the object needs to identify what was viewed. A list of valid values  for the object definition type can be found at (../vocabulary.md#Object.definition.extension)

### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://moodle.data.alpha.jisc.ac.uk/mod/quiz/view.php?id=13"   	 	//  unique id or url of the item being logged into
	"definition": {
		"type": "http://xapi.jisc.ac.uk/define/vle/page",			//  definition type as above
		"name": { "en": "Sample page" },			   //  name of item as returned by VLE
		"description": { "en": "sample page" } //  description of item as returned by VLE
	 }
}
```

### Complete VLE Specific Examples
[Moodle Example](/vle/moodle/moduleview.js)

[Blackboard Example](/vle/blackboard/course_content_access.json)
