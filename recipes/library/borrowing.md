# Borrowed statement template

This statement template is in draft. 

There is not yet a generic statement for this statment. 

[Statement Template Changes](/version_changes.md#borrowed)

## Purpose
This template defines the structure and terms to record the experience of viewing a vle resource such as a Moodle Module or Blackboard building block (eg a page as identified by its url)

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

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
            "homePage": "<iri of system homepage>"
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb,[borrow](/vocabulary.md#verbs), indicates that the actor has borrowed the object. If a target is specified, it identifies the entity from which the object was borrowed. For instance, if a person borrows a book from a library, the person is the actor, the book is the object and the library is the target. 

### Example:

``` javascript
"verb": {
        "id": "http://activitystrea.ms/schema/1.0/borrow",
        "display": {
            "en": "borrowed"
        }
    },
```
### Context
What is the contextual information for this statement?

### Example:

``` javascript

			}
        }
```

### Object

Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

For this statement the object needs to identify what was borrowed. A list of valid values  for the object definition type can be found on the[vocabularies page](/vocabulary.md#Object.definition.extension)

### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "<book uri?>"   	 	
	"definition": {
		"type": "http://id.tincanapi.com/activitytype/book",			
		"name": { "en": "Book" },			   
	 }

    }
}
```
