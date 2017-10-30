# VLE forum post and reply template

## Purpose
This statement defines the structure and terms to record a post or reply to a forum within a VLE.

### Actor

Common entity identifier: [ActorA](../common_structures.md#actora)

#### Entity Example:
The actor entity describes the individual who is making the reply.

``` Javascript
{
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb

Common entity identifier: [VerbA](/common_structures.md#verba)

#### Entity Example:

The verb depends on whether the post starts or continues a discussion.

- The verb [create](/vocabulary.md#create) denotes the action of creating an object, in this case starting a discussion on a forum.
- [replied](/vocabulary.md#replied) denotes the action of replying, in this case replying to a discussion topic on a forum.

``` javascript
"verb": {
        "id": "http://activitystrea.ms/schema/1.0/create",
        "display": {
            "en": "created"
        }
    },

"verb": {
        "id": "http://id.tincanapi.com/verb/replied",
        "display": {
            "en": "replied"
        }
    },
```

### Result
The result.response entity contains plain text from the post encoded as per the encoding of the rest of the statement. There must be no markup,  HTML entity encodings or invalid characters.

<table>
	<tr><th>Property [cardinality]</th><th>Description</th></tr>
	<tr><td>result.response [1]</td><td>Content of post or reply</td></tr>
</table>


#### Entity Example:


``` javascript
 "result":{
        "response":"Does anybody have any good links to this subject?"
    }
```

### Object
Common entity identifier: [ObjectD](/common_structures.md#objectd)

The object definition type depends on whether the statement is about a first post initiating a thread (http://id.tincanapi.com/activitytype/forum-topic), or a reply to an existing thread (http://id.tincanapi.com/activitytype/forum-reply).

#### Entity Example:
The object defines the discussion or thread. The first example is a first post initiating a thread, the second is a reply to an existing thread.

 ``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://moodle2.bolton.ac.uk/mod/forum/discuss.php?d=19474"	
	"definition": {
		"type": "http://id.tincanapi.com/activitytype/forum-topic",			
		"name": { "en": "Forum topic" },			   
	 }
    }
}

"object": {
	"objectType": "Activity",
	"id": "http://moodle2.bolton.ac.uk/mod/forum/discuss.php?d=19474"	
	"definition": {
		"type": "http://id.tincanapi.com/activitytype/forum-reply",			
		"name": { "en": "Forum reply" },			   
	 }
    }
}

```

### Context
The Context describes the parent forum of the thread, and optionally, the courseArea (with module identifiers).

#### Entity Example:

``` javascript
"context": {
    "platform": "Moodle",
    "extensions": {
    		"http://jisc.ac.uk/forumArea": "http://moodle.data.alpha.jisc.ac.uk/mod/forum/view.php?id=138371",
			
		"http://xapi.jisc.ac.uk/courseArea": {
      		 	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
				"http://xapi.jisc.ac.uk/uddModInstanceID": "LA101-200-2016S1-0",
			},
			
	"http://xapi.jisc.ac.uk/sessionId":"32456891",
	"http://id.tincanapi.com/extension/ip-address": "10.3.3.48",
	"http://xapi.jisc.ac.uk/version" : "1.0"
			}
		}
```
