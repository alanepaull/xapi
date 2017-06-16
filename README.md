# xAPI recipes for the Jisc Learning Analytics Project v1.0

## Repository Workflow
The simplest way of contributing xAPI recipes works as follows:

1. Add an issue to the issue tracker to alert everyone to what you are working on and why.
2. Tag the issue with the version milestone you'd like the patch to be a part of.
3. If the feature is for this version then make an edit or add a file in this repository, and save it to your own branch. If you prefer, you can fork the whole repository and work in your own repository. Otherwise create a feature-branch to work in.
4. If you are creating a new statement in a recipe then check if a generic template will help. If you are creating a new statement then consider creating a generic one first.
4. Send a pull request once you're done
5. The pull request will be discussed at our weekly meeting and either merged, or kept in the queue, depending on whether more work is required

You can do all this through the Github GUI, but you're welcome to use any other git tool you prefer.

If the need arises, particular versions will get their own branches, but until that time, everything is merged into the main branch. Releases will be made after the group has come to an agreement.

## Statement Vocabulary and Common Structures

* [Vocabulary](vocabulary.md) gives the IRIs and definitions for verbs, activity types, etc, as well as for extensions used in the recipes.
* [Common Structures](common_structures.md) outlines common patterns used across different recipes.
* [Generic Statement Templates](generic/index.md) can be found in this directory.

# Recipes
Here are descriptions of statements that can be sent to the Jisc LRW, full statement examples, data needed to create the statement.  As far as possible all entities are the same across statements and are identified by a version.

## VLE

These are platform independent statements related to Virtual Learning Enviroments.

<table>
<tr><td>Statement Template </td>   <td>JSON example</td> </tr>
<tr><td> <a href = "/recipes/vle/login.md">Logged in</a></td><td> <a href = "vle/moodle/login.js">Logged in Moodle </a> <br/><a href = "vle/blackboard/loggedin.json"> Logged In Blackboard   </a>   </td> </tr>                                                           
<tr><td> <a href = "/recipes/vle/logout.md">Logged out</a></td><td> <a href = "vle/moodle/logout.js">Logged out Moodle </a>  <br/> <a href = "vle/blackboard/loggedout.json"> Logged out Blackboard   </a>    </td> </tr>    
<tr><td> <a href = "/recipes/vle/Module-View.md">VLE resource viewed   </a></td><td><a href = "vle/moodle/moduleview.js">Moodle module viewed </a> <br/> <a href = "vle/blackboard/course_access.json"> Blackboard course acccess  </a> <br/> <a href="vle/blackboard/course_content_access.json">Blackboard content accessed</a></td> </tr>    
<tr><td> <a href = "/recipes/vle/Session-timeout.md">Session timeout   </a></td><td><a href = "vle/blackboard/session_timeout.json">Blackboard session timeout </a>    </td></tr>    
<tr><td><a href =  "/recipes/vle/assignment-graded.md">Assignment Graded   </a></td><td> <a href = "vle/moodle/asssignment_graded.json">Assignment graded in Moodle</a><br/> <a href="vle/blackboard/asssignment_graded.json">Assignment graded in Blackboard </a>   </td></tr>    
<tr><td><a href =  "/recipes/vle/assignment-submitted.md">Assignment Submitted  </a></td><td><a href = "vle/moodle/assignment_submitted.json">Assignment submitted in Moodle</a><br/> <a href="vle/blackboard/assignment_submitted.json">Assignment submitted in Blackboard</a>   </td></tr>    
<tr><td> <a href = "/recipes/vle/post.md">Post in a forum</a></td><td> </td> </tr>                                                           
<tr><td> <a href = "/recipes/vle/post-reply.md">Replied to post</a></td><td> </td> </tr>    
</table>

### All VLE statement examples
* [Blackboard VLE samples](vle/blackboard/Examples.md)
* [Moodle VLE samples](vle/moodle/examples.md)

## Student Goal app
Statements related to the Student Goal app

## Presence and Attendance
<table>
<tr><td>Statement Template </td><td>JSON Example</td></tr>
<tr><td> <a href = "recipes/attendance/attendance.md">Attended learning activity </a></td><td><a href = "recipes/attendance.md#example">Attended learning activity </a></td> </tr>    
</table>

## Study App
<table>
<tr><td>Statement Template </td><td>JSON Example</td></tr>
<tr><td> <a href = "recipes/studyapps/mobile-app.md">Mobile content viewed </a></td><td><a href = "recipes/studyapps/mobile-app.md#example">Mobile_app content viewed </a></td> </tr>    
</table>

## Tracking App
These will be split into seperate recipe statement templates
<table>
<tr><td>Statement Template </td><td>JSON Example</td></tr>
<tr><td> <a href = "recipes/studyapps/tracker-app.md">Draft tracker activites</a></td><td><a href = "recipes/studyapps/mobile-app.md#example">Draft tracker activites</a></td> </tr>    
</table>

## Predictive Model Output
* [Alerting JSON](/lap/apereo/model_output.js)
* [Alerting](/lap/apereo/model_output.md)

### Library
<table>
<tr><td>Statement Template </td>   <td>JSON example</td> </tr>                                                         
<tr><td> <a href = "/recipes/library/reading-list-view.md">Viewed Reading List</a></td><td>   </td> </tr>                                                           
<tr><td> <a href = "/recipes/library/reading-list-item-view.md">Viewed Reading List item</a></td><td>   </td> </tr>        
<tr><td> <a href = "/recipes/library/econtent.md">Accessing econtent</a></td><td></td></tr>        
<tr><td> <a href = "/recipes/library/borrowing.md">Borrowed item</a></td><td></td> </tr>        
<tr><td> <a href = "/recipes/library/login.md">Login to system</a></td><td>  </td> </tr>        
</table>
