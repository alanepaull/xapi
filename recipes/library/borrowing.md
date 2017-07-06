# Borrowed statement template

This statement template is in draft. 

There is not yet a generic statement for this statment. 

[Statement Template Changes](/version_changes.md#borrowed)

## Draft Notes

The following draft needs updating with Jisc who are in conversation with vendors

The following headings haven't made their way  into the statement yet. Need expanding with the Jisc library team.

- Event Staff Full Name string name for librarian processing request
- Patron Barcode identifier for borrower, x-ref udd
- Patron Custom Category 1 custom, repeats of info from UDD
- Patron Custom Category 2 custom, repeats of info from UDD
- Patron Custom Category 3 custom, repeats of info from UDD
- Patron Custom Category 4 custom, repeats of info from UDD
- Item Permanent Shelving Location string (object)
- Item Temporary Shelving Location string (object)

Minted IRIS have taken the approach of the attendance statement, library_iri_information

Decisions around id uris etc need to be discussed

## Purpose
This template defines the structure and terms to record the experience of viewing a vle resource such as a Moodle Module or Blackboard building block (eg a page as identified by its url)

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

The actor entity describes the individual that is borrowing an item.

### Example:

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "<iri of system homepage>" // what
        }
    },
```

### Verb
- Event Type e.g. checkout, renewal (verb)

Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb depends upon the action. 

-  http://activitystrea.ms/schema/1.0/borrowed [borrowed](/vocabulary.md#verbs), indicates that the actor has borrowed the object.
-  http://xapi.jisc.ac.uk/renewed [renewed](/vocabulary.md#verbs), indicates that the actor has renewed the object.
-  http://activitystrea.ms/schema/1.0/return [returned](/vocabulary.md#verbs), indicates that the actor has returned the object.

### Example:

``` javascript
"verb": {
        "id": "http://activitystrea.ms/schema/1.0/borrow",
        "display": {
            "en": "borrowed"
        }
    },
```


### Object

Item Material Format e.g. book, journal object)
Item Branch Name see event branch name, e.g. main library (is this different from event branch name? 

Common entity identifier: ObjectA, as defined on the [common structures](/common_structures.md#objecta) page.

For this statement the object needs to identify what was borrowed. A list of valid values for the object definition type can be found on the[vocabularies page](/vocabulary.md#Object.definition.extension)
Examples of valid definition types:

- Book http://id.tincanapi.com/activitytype/book
- Electronic content http://xapi.jisc.ac.uk/eContent ?
- Journal http://xapi.jisc.ac.uk/journal (is there not something better than self minted)?


### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://library.universityofjisc.ac.uk/978-3-16-148410-0"   	(what would the iri of a book look like? http://classify.oclc.org/classify2/ClassifyDemo?owi=13447796) 	
	"definition": {
		"type": "http://id.tincanapi.com/activitytype/book",	(How do we work out from the data the type?)		
		"name": { "en": "Intro to Java" },			   
	 }
	
	extensions{
	
		"http://id.tincanapi.com/extension/isbn": "978-3-16-148410-0"
		"http://xapi.jisc.ac.uk/library_ddc": "614"
		"http://xapi.jisc.ac.uk/library_oclc": "13447796"
	
    }
}
```

### Timestamp

- Event Date (timestamp)
- Event Day Name of Week e.g. Tuesday (timestamp)

An ISO 8601 format timestamp that corresponds to the time of when the item was borrowed.

### Example:

``` javascript
"timestamp": "2015-09-18T01:54:51.484Z",
```


### Context

### Example:

``` javascript
"context": {
 
  "extensions": {
	"http://xapi.jisc.ac.uk/library_borrower_category": "UG", // should this be a code
    "http://xapi.jisc.ac.uk/library_loan_policy": "short", // should this be a code
    "http://xapi.jisc.ac.uk/library_branch" : "Main library",  // should this be a code
	"http://xapi.jisc.ac.uk/library_return_date" : "2015-09-18T01:54:51.484Z"  //(should this be a code)
	"http://xapi.jisc.ac.uk/library_renew_count" : "3"  
	
  }
}
```
