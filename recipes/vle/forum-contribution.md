#vle_forum_contribution statement template
Revision: 0.1

##Purpose
This template defines the structure and terms to record the experience of contributing to a forum.

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

The actor entity describes the individual that is making a forum contribution.

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
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.


### Example:


### Context
Common entity identifier: ContextA, as defined on the [common structures](/common_structures.md#contextc) page.

The courseArea is required. See the [vocabularies](../vocabulary.md#42-coursearea-properties) page for more information

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
			"http://xapi.jisc.ac.uk/recipeVersion" : "vle_forum_contributionv0.1"
			
			}
              
        }
```

### Object

### Example

### Complete VLE Specific Examples

