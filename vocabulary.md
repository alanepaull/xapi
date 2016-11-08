---
layout: home
---

# JISC Learning Analytics Statements and Vocabulary
The following terms are in use in the Jisc learning analytics recipes.
NOTE: The xapi.jisc.ac.uk namespace URI may change.

## 1.0 Verb

Example of a verb entity, this example uses 'en' language tag, but any RFC 5646 language tag can be used: 

``` javascript
"verb": {
        "id": "https://brindlewaye.com/xAPITerms/verbs/loggedin",
        "display": {
            "en" : "logged in to"
        }
    },
``` 

The following [xAPI verbs](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.html#verb) are defined as part of the Jisc profile:

### Logged in
<table>
<tr><th align="left">Verb</th><td>Logged in</td></tr>
<tr><th align="left">Description</th><td>Logged in to some service </td></tr>
<tr><th align="left">IRI</th><td> <a href="https://brindlewaye.com/xAPITerms/verbs/loggedin"> https://brindlewaye.com/xAPITerms/verbs/loggedin </a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/login.html#verb">Logged in</a> </td></tr>
</table>

### Logged out
<table>
<tr><th align="left">Verb</th><td>Logged out</td></tr>
<tr><th align="left">Description</th><td>Logged out of some service</td></tr>
<tr><th align="left">IRI</th><td> <a href="https://brindlewaye.com/xAPITerms/verbs/loggedout"> https://brindlewaye.com/xAPITerms/verbs/loggedout </a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/logout.html#verb">Logged out</a> </td></tr>
</table>

### Viewed
<table>
<tr><th align="left">Verb</th><td>Viewed</td></tr>
<tr><th align="left">Description</th><td>Indicates that the actor has viewed the object</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/verb/viewed"> http://id.tincanapi.com/verb/viewed</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/Module-View.html#verb">Object Viewed</a> </td></tr>
</table>

### Session timed out
<table>
<tr><th align="left">Verb</th><td>Session timed out</td></tr>
<tr><th align="left">Description</th><td>IIndicates the activity provider has determined that the session was abnormally terminated either by an actor or due to a system failure. </td></tr>
<tr><th align="left">IRI</th><td> <a href="https://w3id.org/xapi/adl/verbs/abandoned">https://w3id.org/xapi/adl/verbs/abandoned</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/Session-timeout.html#verb">Session Timeout</a> </td></tr>
</table>

### Completed
<table>
<tr><th align="left">Verb</th><td>Completed</td></tr>
<tr><th align="left">Description</th><td>Completing an activity - finishing in its entirety</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://adlnet.gov/expapi/verbs/completed">http://adlnet.gov/expapi/verbs/completed</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/assignment-submitted.html">Assignment submitted</a> </td></tr>
</table>

### Scored
<table>
<tr><th align="left">Verb</th><td>Scored</td></tr>
<tr><th align="left">Description</th><td>Indicates a numerical value related to an actor's performance on an activity.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://adlnet.gov/expapi/verbs/scored">http://adlnet.gov/expapi/verbs/scored</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/assignment-graded.html#verb">Assignment Graded</a> </td></tr>
</table>

### Attended
<table>
<tr><th align="left">Verb</th><td>Attended</td></tr>
<tr><th align="left">Description</th><td>Indicates the actor was present at a virtual or physical event or activity.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://adlnet.gov/expapi/verbs/attended">http://adlnet.gov/expapi/verbs/attended</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/attended.html#verb">Attended learning activity</a> </td></tr>
</table>

## 2.0 Result

In the Jisc profile, the use of the [result entity](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.html#result) and any of its properties is optional. Such as in the [recipes/assignment-graded.html#verb](assignment graded recipe#result) recipe example.

Example:


``` javascript
 "result":{
        "score":{
            "raw":8
                }
        "extensions": {
        	"http://xapi.jisc.ac.uk/grade":"5 stars"
        	}
    },
```

### 2.1 Result Extensions

The following are extension properties in the result entity:

### Grade

<table>
<tr><th align="left">Label</th><td>Scored</td></tr>
<tr><th align="left">Description</th><td>A non-numerical assessment result. Data type is string (256)</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/grade">http://xapi.jisc.ac.uk/grade</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/assignment-graded.html#verb">Assignment Graded</a> </td></tr>
<tr><th align="left">Value Space</th><td>String</td></tr>
<tr><th align="left">Sample Value</th><td>5 Stars</td></tr>
</table>


## 3.0 Object


### 3.1 Activity Types
The following are types of the [Activity Definition Object](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.html#activity-definition). 

Example:
``` javascript
"object": {
	"objectType": "Activity",
	"id": "http://moodle.data.alpha.jisc.ac.uk/mod/quiz/view.php?id=13" 
	"definition": {
		"type": "http://xapi.jisc.ac.uk/define/vle/page",			//  activity type 
		"name": { "en": "Sample page" },			   
		"description": { "en": "sample page" } 
	 }
}
```


### Application

<table>
<tr><th align="left">Label</th><td>Application</td></tr>
<tr><th align="left">Description</th><td>Represents any kind of software application</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://activitystrea.ms/schema/1.0/application">http://activitystrea.ms/schema/1.0/application</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/login.html#complete_example">Logged in</a> </td></tr>
</table>

### Assessment

<table>
<tr><th align="left">Label</th><td>Application</td></tr>
<tr><th align="left">Description</th><td>An assessment is an activity type that determines a learner’s mastery of a particular subject area. An assessment typically has one or more questions.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://adlnet.gov/expapi/activities/assessment">http://adlnet.gov/expapi/activities/assessment</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/assignment-submitted.html">assignment-submitted</a> </td></tr>
</table>


### Course

<table>
<tr><th align="left">Label</th><td>Course</td></tr>
<tr><th align="left">Description</th><td>A course represents an entire “content package” worth of material. The largest level of granularity. Unless flat, a course consists of multiple modules.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://adlnet.gov/expapi/activities/course">http://adlnet.gov/expapi/activities/course</a> </td></tr>
</table>


### Module

<table>
<tr><th align="left">Label</th><td>Module</td></tr>
<tr><th align="left">Description</th><td>A module represents any “content aggregation” at least one level below the course level. Modules of modules can exist for layering purposes. Modules are not content. Modules are one level up from all content. </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://adlnet.gov/expapi/activities/module">http://adlnet.gov/expapi/activities/module</a> </td></tr>
<tr><th align="left">Recipe Example</th><td> <a href="recipes/Module-View.html#object">Module-View</a> </td></tr>
</table>

### VLE

<table>
<tr><th align="left">Label</th><td>VLE</td></tr>
<tr><th align="left">Description</th><td>Learning Management System. At it's core, a platform used to launch and track learning experiences.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/activitytype/lms ">http://id.tincanapi.com/activitytype/lms </a> </td></tr>
</table>

### VLE content

<table>
<tr><th align="left">Label</th><td>VLE content</td></tr>
<tr><th align="left">Description</th><td>Any generic resource in a VLE</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/vle/content">http://xapi.jisc.ac.uk/vle/content</a> </td></tr>
</table>

### VLE page

<table>
<tr><th align="left">Label</th><td>VLE Page</td></tr>
<tr><th align="left">Description</th><td>Any page within a VLE that isn't designed to be learning content. e.g. navigation or administration pages   </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/vle/page">http://xapi.jisc.ac.uk/vle/page</a> </td></tr>
<tr><th align="left">Example in Recipe</th><td> <a href="recipes/Module-View.html#object">Module-View</a> </td></tr>
<tr><th align="left">UI Example</th><td> <a href="http://moodle.data.alpha.jisc.ac.uk/mod/page/view.php?id=9">A page on University of Jisc</a> </td></tr>
</table>

### VLE Quiz

<table>
<tr><th align="left">Label</th><td>VLE Quiz</td></tr>
<tr><th align="left">Description</th><td>Quiz within a VLE</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/vle/quiz">http://xapi.jisc.ac.uk/vle/quiz</a> </td></tr>
<tr><th align="left">Example in Recipe</th><td> <a href="recipes/Module-View.html#object">Module-View</a> </td></tr>
<tr><th align="left">UI Example</th><td> <a href="http://moodle.data.alpha.jisc.ac.uk/mod/page/view.php?id=13">A quiz on University of Jisc</a> </td></tr>
</table>

### VLE Forum

<table>
<tr><th align="left">Label</th><td>VLE forum</td></tr>
<tr><th align="left">Description</th><td>A VLE forum/discussion board</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/vle/forum">http://xapi.jisc.ac.uk/vle/forum</a> </td></tr>
<tr><th align="left">UI Example (Moodle)</th><td> <a href="http://moodle.data.alpha.jisc.ac.uk/mod/forum/view.php?id=12">A forum on University of Jisc</a> </td></tr>
<tr><th align="left">UI Example (Blackboard)</th><td> <a href="https://jisc.blackboard.com/webapps/discussionboard/do/forum?action=list_threads&course_id=_144_1&forum_id=81&nav=discussion_board&conf_id=_164_1&content_id=_218_1&mode=view)">A discussion board on University of Jisc</a> </td></tr>
</table>

### External URL

<table>
<tr><th align="left">Label</th><td>External URL</td></tr>
<tr><th align="left">Description</th><td>An external URL</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/externalURL">http://xapi.jisc.ac.uk/externalURL</a> </td></tr>
</table>

### File

<table>
<tr><th align="left">Label</th><td>File</td></tr>
<tr><th align="left">Description</th><td>Accessing any kind of non-web native file type. e.g. MS office, video or audio. </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/vle/file">http://xapi.jisc.ac.uk/vle/file</a> </td></tr>
</table>

### Lecture

<table>
<tr><th align="left">Label</th><td>Lecture</td></tr>
<tr><th align="left">Description</th><td>A learning activity that consists mainly of an expert giving a talk to a number of learners.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/lecture">http://xapi.jisc.ac.uk/lecture</a> </td></tr>
</table>

### Tutor session

<table>
<tr><th align="left">Label</th><td>Tutor session</td></tr>
<tr><th align="left">Description</th><td>This represents a tutoring session.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/activitytype/tutor-session">http://id.tincanapi.com/activitytype/tutor-session</a> </td></tr>
</table>

### Event

<table>
<tr><th align="left">Label</th><td>Event</td></tr>
<tr><th align="left">Description</th><td>Any event.<br/>The "event" Activity Type should only be used when the type of event is unspecified.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://activitystrea.ms/schema/1.0/event">http://activitystrea.ms/schema/1.0/event</a> </td></tr>
</table>

## 3.2 Object Definition Extensions
The following are Jisc profile extensions to be used in [object.definition.extensions](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.html#object). See the [Assignment Graded](recipes/assignment-graded.html#verb)

### Due Date

<table>
<tr><th align="left">Label</th><td>Due Date</td></tr>
<tr><th align="left">Description</th><td>Date object is due to be submitted. Format is ISO 8601 date time . </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/dueDate">http://xapi.jisc.ac.uk/dueDate</a> </td></tr>
<tr><th align="left">Example in Recipe</th><td> <a href="v0.3/recipes/assignment-graded.html#object">assignment-graded</a> </td></tr>
<tr><th align="left">Data Type</th><td>String</td></tr>
<tr><th align="left">Value Space</th><td>ISO 8601 date time</td></tr>
<tr><th align="left">Sample Value</th><td>2016-02-05T17:59:45.000Z</td></tr>
</table>

### DateTime

<table>
<tr><th align="left">Label</th><td>DateTime</td></tr>
<tr><th align="left">Description</th><td>Value representing a calendar date and time, such as 2013-08-27 09:26:45.001. Value should be a string formatted as an ISO8601 date and time to match the rest of the specification values.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/extension/datetime">http://id.tincanapi.com/extension/datetime</a> </td></tr>
<tr><th align="left">Example in Recipe</th><td> <a href="recipes/attendance.html#object">attendance</a> </td></tr>
<tr><th align="left">Data Type</th><td>String</td></tr>
<tr><th align="left">Value Space</th><td>ISO 8601 date time</td></tr>
<tr><th align="left">Sample Value</th><td>2016-02-05T17:59:45.000Z</td></tr>
</table>

### Duration

<table>
<tr><th align="left">Label</th><td>Duration</td></tr>
<tr><th align="left">Description</th><td>Value representing a length of time, for example the length of a video. Value should be formatted as an ISO8601 duration to match the Result.duration property. Note that ISO8601 duration allows representations to extend beyond their carry over points. e.g. one and a half hours can be represented as either PT1H30M0S or PT90M. This extension will generally be used within an Activity Definition to indicate a length of an Activity as compared to the Result.duration which captures the length of time for a specific event. For example a video may be 5 minutes long (this Extension), but an actor may have only watched 30 seconds of it (the Result.duration). </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/extension/duration">http://id.tincanapi.com/extension/duration</a> </td></tr>
<tr><th align="left">Example in Recipe</th><td> <a href="recipes/attendance.html#object">attendance</a> </td></tr>
<tr><th align="left">Data Type</th><td>String</td></tr>
<tr><th align="left">Value Space</th><td>ISO 8601 duration</td></tr>
<tr><th align="left">Sample Value</th><td>PT1H30M0S</td></tr>
</table>

### Application Type

Was used in older recipes to identify the genre of software application. Best practice is to use subType instead.

<table>
<tr><th align="left">Label</th><td>Application Type </td></tr>
<tr><th align="left">Description</th><td>Identifies the genre of software application </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/applicationType">http://xapi.jisc.ac.uk/applicationType</a> </td></tr>
<tr><th align="left">Example in Recipe</th><td> <a href="recipes/login.html#object">Logged in</a> </td></tr>
<tr><th align="left">Data Type</th><td>IRI</td></tr>
<tr><th align="left">Sample Value</th><td>http://id.tincanapi.com/activitytype/lms</td></tr>
</table>

### Sub Type

<table>
<tr><th align="left">Label</th><td>Sub Type </td></tr>
<tr><th align="left">Description</th><td>Identifies the sub genre of any application </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/subType">http://xapi.jisc.ac.uk/subType</a> </td></tr>
<tr><th align="left">Example in Recipe</th><td> <a href="recipes/login.html#object">Logged in</a> </td></tr>
<tr><th align="left">Data Type</th><td>IRI or String</td></tr>
<tr><th align="left">Sample Value</th><td>http://id.tincanapi.com/activitytype/lms</td></tr>
</table>

### UDD Module Instance ID

<table>
<tr><th align="left">Label</th><td>UDD Module Instance ID</td></tr>
<tr><th align="left">Description</th><td>An identifier for a module instance<br/>The value should correspond to the [UDD module_instance.MOD_INSTANCE_ID](https://github.com/jiscdev/analytics-udd/blob/master/udd/module_instance.html#mod_instance_id) identifier that identifies the relevant module in UDD compliant data.</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/uddModInstanceID">http://xapi.jisc.ac.uk/uddModInstanceID</a> </td></tr>
</table>


## 4.0 Context


## 4.1 Context Extensions
The following are properties of the [Context extensions property](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI-Data.html#246-context).

### Umbrella course area

For more information see Jisc profile [CourseArea properties](#42-coursearea-properties).

<table>
<tr><th align="left">Label</th><td>Umbrella course area</td></tr>
<tr><th align="left">Description</th><td> Umbrella course/parent area by its home page URI </td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/courseArea">http://xapi.jisc.ac.uk/courseArea</a> </td></tr>
<tr><th align="left">Data Type</th><td>A JSON Object</td></tr>
<tr><th align="left">Value Space</th><td>JSON Object with properties vle_mod_id and/or id </td></tr>
<tr><th align="left">Sample Value</th><td> {

 "http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
 "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"}"
 
 </td></tr>
</table>

### Session id

<table>
<tr><th align="left">Label</th><td>Session id</td></tr>
<tr><th align="left">Description</th><td>local session id</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/sessionId">http://xapi.jisc.ac.uk/sessionId</a> </td></tr>
<tr><th align="left">Data Type</th><td>String</td></tr>
<tr><th align="left">Value Space</th><td>Session id as reported by the VLE</td></tr
<tr><th align="left">Sample Value</th><td>32456891</td></tr>
</table>

### IP address

<table>
<tr><th align="left">Label</th><td>Session id</td></tr>
<tr><th align="left">Description</th><td>client's address location on internet</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://id.tincanapi.com/extension/ip-address">http://id.tincanapi.com/extension/ip-address</a> </td></tr>
<tr><th align="left">Data Type</th><td>String </td></tr>
<tr><th align="left">Value Space</th><td>(IP address) in either IPv4 or IPv6 format</td></tr>
<tr><th align="left">Sample Value</th><td>10.3.3.48</td></tr>
</table>


### Recipe Version

<table>
<tr><th align="left">Label</th><td>Recipe Version</td></tr>
<tr><th align="left">Description</th><td>Version of Recipe used. Version number can be found on recipe page</td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/recipeVersion">http://xapi.jisc.ac.uk/recipeVersion</a> </td></tr>
<tr><th align="left">Data Type</th><td>String</td></tr>
<tr><th align="left">Value Space</th><td>Version number found on recipe page, follows Semantic versioning.</td></tr>
<tr><th align="left">Sample Value</th><td>1.0</td></tr>
</table>

## 4.2 CourseArea properties
The following are properties of the profile extension context.extensions.courseArea
 
### VLE Module ID

http://xapi.jisc.ac.uk/extensions/vle_mod_id is a courseArea identifier. It is used in the module_VLE_map entity of the UDD to link module instances to course areas. Note that several module instances (as identified by their UDD MOD_INSTANCE_ID) can link to one courseArea. 

<table>
<tr><th align="left">Label</th><td>VLE Module ID</td></tr>
<tr><th align="left">Description</th><td><a href="https://github.com/jiscdev/analytics-udd/blob/master/udd/module_vle_map.html">Entity that connects a course area in a VLE with a module</a></td></tr>
<tr><th align="left">IRI</th><td> <a href="http://xapi.jisc.ac.uk/vle_mod_id">http://xapi.jisc.ac.uk/vle_mod_id</a> </td></tr>
</table>

## 5.0 Version Changes and identifier mappings

### v0.2


| V0.1  		| v0.2                    		 | 
| ------------- | -------------------------------|
| http://xapi.jisc.ac.uk/define/extensions/vle/content  | http://xapi.jisc.ac.uk/vle/content
| http://xapi.jisc.ac.uk/define/extensions/vle/page     | http://xapi.jisc.ac.uk/vle/page  
| http://xapi.jisc.ac.uk/define/extensions/vle/quiz     | http://xapi.jisc.ac.uk/vle/quiz  
| http://xapi.jisc.ac.uk/define/extensions/vle/forum    | http://xapi.jisc.ac.uk/vle/forum  
| http://xapi.jisc.ac.uk/define/extensions/externalURL  | http://xapi.jisc.ac.uk/externalURL
| http://xapi.jisc.ac.uk/extensions/courseArea | http://xapi.jisc.ac.uk/courseArea	
| http://xapi.jisc.ac.uk/extensions/sessionId  | http://xapi.jisc.ac.uk/sessionId 
| http://xapi.jisc.ac.uk/extensions/recipeVersion | http://xapi.jisc.ac.uk/recipeVersion
| http://xapi.jisc.ac.uk/extensions/applicationType | http://xapi.jisc.ac.uk/applicationType
| http://xapi.jisc.ac.uk/extensions/duedate  | http://xapi.jisc.ac.uk/dueDate
| http://xapi.jisc.ac.uk/define/vle   		 | http://id.tincanapi.com/activitytype/lms        
| http://www.tincanapi.co.uk/verbs/evaluated | http://adlnet.gov/expapi/verbs/scored 
