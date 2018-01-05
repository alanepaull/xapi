# borrowed statement template

[Statement Template Changes](/version_changes.md#borrowed)

## Purpose
This template defines the structure and terms to record the experience of viewing a vle resource such as a Moodle Module or Blackboard building block (eg a page as identified by its url)

### Actor
Common entity identifier:  ActorA, as defined on the [common structures](/common_structures.md#actora) page.

### Example:

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "PATRON_BARCODE",
            "homePage": "HOMEPAGE" 
        }
    },
```

### Verb
Common entity identifier: VerbA, as defined on the [common structures](/common_structures.md#verba) page.

The Verb depends upon the action that is taking place. The following are allowed verbs in  borrwed statements.

<table>
<tr><td>Verb</td><td>usage</td></tr>
<tr><td>http://activitystrea.ms/schema/1.0/borrowed</td><td>Indicates that the actor has borrowed the object.</td></tr>
<tr><td>http://xapi.jisc.ac.uk/renewed</td><td>Indicates that the actor has renewed the object</td></tr>
<tr><td>http://activitystrea.ms/schema/1.0/return </td><td>Indicates that the actor has returned the object.</td></tr>
</table>


### Example:

``` javascript
"verb": {
        "id": "http://activitystrea.ms/schema/1.0/borrowed",
        "display": {
            "en": "borrowed"
        }
    },
```


### Object
Draft notes: While in draft the following iri's have been used: and will be added to the vocab

<table>
<td>ActivityType</td><td>usage</td>
<tr><td>http://id.tincanapi.com/activitytype/book</td><td>Book.</td></tr>
<tr><td>http://id.tincanapi.com/activitytype/resource </td><td>Resource</td></tr>
<tr><td>http://xapi.jisc.ac.uk/journal</td><td>Journal</td></tr>
</table>


<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Value information</</th></tr>
	<tr>
		<td>object.objectType [1]</td>
		<td>The value must be "Activity".</td>
		<td>String, value must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id [1]</td>
		<td>An identifier for the object of the xAPI statement. This must be unique across all object types.</td>
		<td>iri</td>
	</tr>
	<tr>
		<td>object.definition.type [1]</td>
		<td>Indicates the type of the object of the statement. It is required and valid values are listed on the <a href="vocabulary.md#activity-types">vocabulary page</a></td>
		<td>iri</td>
	</tr>
	<tr>
		<td>object.definition.name [0..1]</td>
		<td>Optional object name</td>
		<td>string</td>
	</tr>
	<tr>
		<td>object.definition.extensions.http://xapi.jisc.ac.uk/subType [0..1]</td>
		<td>May be used to indicate the sub-type of this activity, if applicable for the recipe being used to create the statement. This qualifies the object.objectType, and is described on the [vocabularies](vocabulary.md#object-definition-extensions) page.</td>
		<td>iri</td>
	</tr>
	<tr>
		<td>extensions.http://oclc.com/number</td>
		<td>OCLC Number</td>
		<td>string</td>
	</tr>
		<tr>
		<td>extensions.http://xapi.jisc.ac.uk/dewey_code"</td>
		<td>Dewey Decimal Code</td>
		<td>string</td>
	</tr>
	<tr>
		<td>extensions.http://xapi.jisc.ac.uk/item_location</td>
		<td>Item locatition contains 3 properties, all of which are strings: http://id.tincanapi.com/extension/location , http://xapi.jisc.ac.uk/permanent_shelving" and http://xapi.jisc.ac.uk/temporary_shelving"</td>
		<td>JSON Object</td>
	</tr>
</table>


### Example

``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://library.universityofjisc.ac.uk/0123456789" 	
	"definition": {
		"type": "http://id.tincanapi.com/activitytype/book",	
		"name": { "en": "Intro to Java" },			   
	 }
	
	"extensions": {
		"http://oclc.com/number": "OCLC_NUMBER",
		"http://xapi.jisc.ac.uk/dewey_code": "CALL_NUMBER"
		"http://xapi.jisc.ac.uk/item_location": {
				"http://id.tincanapi.com/extension/location": "ITEM_BRANCH_NAME",
				"http://xapi.jisc.ac.uk/permanent_shelving": "ITEM_PERMANENT_SHELVING_LOCATION",
				"http://xapi.jisc.ac.uk/temporary_shelving": "ITEM_TEMPORARY_SHELVING_LOCATION"
			},
			
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


<table>
	<tr><th>Property [cardinality]</th><th>Description</th><th>Value information</</th></tr>
	<tr>
		<td>context.extensions.http://xapi.jisc.ac.uk/library_borrower_category</td>
		<td>Borrower category, from institutional defined list</td>
		<td>string</td>
	</tr>
	<tr>
		<td>context.extensions.http://xapi.jisc.ac.uk/library_loan_policy</td>
		<td>Loan policy, from institutional defined list</td>
		<td>string</td>
	</tr>
		<tr>
		<td>context.extensions.http://xapi.jisc.ac.uk/library_branch</td>
		<td>Library branch</td>
		<td>string</td>
	</tr>
	<tr>
		<td>context.extensions.http://xapi.jisc.ac.uk/library_return_date</td>
		<td>ISO 8601 date time</td>
		<td>string</td>
	</tr>
	<tr>
		<td>context.extensions.http://xapi.jisc.ac.uk/library_renew_count</td>
		<td>Renew count</td>
		<td>string</td>
	</tr>
	<tr>
		<td>context.extensions.version [0..1]</td>
		<td>Recommended, identifies the version of the Jisc xAPI profile found on the ReadMe page. <br/></td>
		<td>string</td>
	</tr>
</table>




### Example:

``` javascript
"context": {
 
  "extensions": {
  
	"http://xapi.jisc.ac.uk/library_borrower_category": "UG", 
    	"http://xapi.jisc.ac.uk/library_loan_policy": "short", 
    	"http://xapi.jisc.ac.uk/library_branch" : "Main library", 
		"http://xapi.jisc.ac.uk/library_return_date" : "2015-09-18T01:54:51.484Z"  
	"http://xapi.jisc.ac.uk/library_renew_count" : 3 
	"http://xapi.jisc.ac.uk/version": "1.0.1"
	
  }
}
```

### Full Example:
``` javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "PATRON_BARCODE",
            "homePage": "HOMEPAGE" 
        }
    },
	"verb": {
        "id": "http://activitystrea.ms/schema/1.0/borrowed",
        "display": {
            "en": "borrowed"
        }
    },
	"object": {
		"objectType": "Activity",
		"id": "http://library.universityofjisc.ac.uk/0123456789"   	
		"definition": {
			"type": "http://id.tincanapi.com/activitytype/book",	
			"name": { "en": "Intro to Java" },			   
		 }
		
		"extensions": {
			"http://oclc.com/number": "OCLC_NUMBER",
			"http://xapi.jisc.ac.uk/dewey_code": "CALL_NUMBER"
			"http://xapi.jisc.ac.uk/item_location": {
					"http://id.tincanapi.com/extension/location": "ITEM_BRANCH_NAME",
					"http://xapi.jisc.ac.uk/permanent_shelving": "ITEM_PERMANENT_SHELVING_LOCATION",
					"http://xapi.jisc.ac.uk": "ITEM_TEMPORARY_SHELVING_LOCATION"
				},
				
			}
	},
	"timestamp": "2015-09-18T01:54:51.484Z",
	"context": {
 
		"extensions": {
  
			"http://xapi.jisc.ac.uk/library_borrower_category": "UG",
			"http://xapi.jisc.ac.uk/library_loan_policy": "short", 
			"http://xapi.jisc.ac.uk/library_branch" : "Main library", 
			"http://xapi.jisc.ac.uk/library_return_date" : "2015-09-18T01:54:51.484Z"  
			"http://xapi.jisc.ac.uk/library_renew_count" : 3 
			"http://xapi.jisc.ac.uk/version": "1.0.1"
	
  }
}
```