# e-content viewed statement template


This statement template is in draft. 

Based on generic template statement: [Viewed](/generic/view.md)

[Statement Template Changes](/version_changes.md#econtent)

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
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "<iri of homepage>"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb,[viewed](/vocabulary.md#verbs) denotes the action of the user's browser or app requesting the econtent.

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
Common entity identifier:


### Example:

``` javascript
"context": {
   
			
        }
```

### Object



### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "<iri of reading list>"   	 	
	"definition": {
		"type": "",			
		"name": { "en": "Sample page" },			   
	 }
	 "extensions": {
     		 "http://xapi.jisc.ac.uk/subType": ""
	 }
    }
}
```


