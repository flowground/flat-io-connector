# ![LOGO](logo.png) Flat **flow**ground Connector

## Description

A generated **flow**ground connector for the Flat API (version 2.7.0).

Generated from: https://api.apis.guru/v2/specs/flat.io/2.7.0/swagger.json<br/>
Generated at: 2019-06-06T16:12:22+03:00

## API Description

The Flat API allows you to easily extend the abilities of the [Flat Platform](https://flat.io), with a wide range of use cases including the following:

* Creating and importing new music scores using MusicXML, MIDI, Guitar Pro (GP3, GP4, GP5, GPX, GP), PowerTab, TuxGuitar and MuseScore files
* Browsing, updating, copying, exporting the user's scores (for example in MP3, WAV or MIDI)
* Managing educational resources with Flat for Education: creating & updating the organization accounts, the classes, rosters and assignments.

The Flat API is built on HTTP. Our API is RESTful It has predictable resource URLs. It returns HTTP response codes to indicate errors. It also accepts and returns JSON in the HTTP body.
The [schema](/swagger.yaml) of this API follows the [OpenAPI Initiative (OAI) specification](https://www.openapis.org/), you can use and work with [compatible Swagger tools](http://swagger.io/open-source-integrations/).
This API features Cross-Origin Resource Sharing (CORS) implemented in compliance with [W3C spec](https://www.w3.org/TR/cors/).

You can use your favorite HTTP/REST library for your programming language to use Flat's API. This specification and reference is [available on Github](https://github.com/FlatIO/api-reference).

Getting Started and learn more:

* [API Overview and interoduction](https://flat.io/developers/docs/api/)
* [Authentication (Personal Access Tokens or OAuth2)](https://flat.io/developers/docs/api/authentication.html)
* [SDKs](https://flat.io/developers/docs/api/sdks.html)
* [Rate Limits](https://flat.io/developers/docs/api/rate-limits.html)
* [Changelog](https://flat.io/developers/docs/api/changelog.html)


## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### List the classes available for the current user

*Tags:* `Class`

#### Input Parameters
* `state` - _optional_ - Filter the classes by state
    Possible values: active, inactive, archived.

### Create a new class

> Classrooms on Flat allow you to create activities with assignments and post content to a specific group.<br/>
> <br/>
> When creating a class, Flat automatically creates two groups: one for the teachers of the course, one for the students. The creator of this class is automatically added to the teachers group.<br/>
> <br/>
> If the classsroom is synchronized with another application like Google Classroom, some of the meta information will automatically be updated.<br/>
> <br/>
> You can add users to this class using `POST /classes/{class}/users/{user}`, they will automatically added to the group based on their role on Flat. Users can also enroll themselves to this class using `POST /classes/enroll/{enrollmentCode}` and the `enrollmentCode` returned in the `ClassDetails` response.

*Tags:* `Class`

### Join a class

> Use this method to join a class using an enrollment code given one of the teacher of this class. This code is also available in the `ClassDetails` returned to the teachers when creating the class or listing / fetching a specific class.<br/>
> <br/>
> Flat will automatically add the user to the corresponding class group based on this role in the organization.

*Tags:* `Class`

#### Input Parameters
* `enrollmentCode` - _required_ - The enrollment code, available to the teacher in `ClassDetails`


### Get the details of a single class

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class

### Update the class

> Update the meta information of the class

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class

### Activate the class

> Mark the class as `active`. This is mainly used for classes synchronized from Clever that are initially with an `inactive` state and hidden in the UI.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class

### Unarchive the class

> Mark the class as `active`. When this course is synchronized with another app, like Google Classroom, this state will be automatically be updated.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class

### Archive the class

> Mark the class as `archived`. When this course is synchronized with another app, like Google Classroom, this state will be automatically be updated.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class

### Assignments listing

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class

### Assignment creation

> Use this method as a teacher to create and post a new assignment to a class.<br/>
> <br/>
> If the class is synchronized with Google Classroom, the assignment will be automatically posted to your Classroom course.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class

### Copy an assignment

> Copy an assignment to a specified class.<br/>
> <br/>
> If the original assignment has a due date in the past, this new assingment will be created without a due date.<br/>
> <br/>
> If the new class is synchronized with an external app (e.g. Google Classroom), the copied assignment will also be posted on the external app.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `assignment` - _required_ - Unique identifier of the assignment

### List the students' submissions

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `assignment` - _required_ - Unique identifier of the assignment

### Create or edit a submission

> Use this method as a student to create, update and submit a submission related to an assignment. Students can only set `attachments`, `studentComment` and `submit`.<br/>
> <br/>
> Teachers can use `PUT /classes/{class}/assignments/{assignment}/submissions/{submission}` to update a submission by id.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `assignment` - _required_ - Unique identifier of the assignment

### Get a student submission

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `assignment` - _required_ - Unique identifier of the assignment
* `submission` - _required_ - Unique identifier of the submission

### Edit a submission

> Use this method as a teacher to update the different submission and give feedback.<br/>
> Teachers can only set `returnFeedback`

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `assignment` - _required_ - Unique identifier of the assignment
* `submission` - _required_ - Unique identifier of the submission

### List the submissions for a student

> Use this method as a teacher to list all the assignment submissions sent by a student of the class

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `user` - _required_ - Unique identifier of the user

### Remove a user from the class

> This method can be used by a teacher to remove a user from the class, or by a student to leave the classroom.<br/>
> <br/>
> Warning: Removing a user from the class will remove the associated resources, including the submissions and feedback related to these submissions.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `user` - _required_ - Unique identifier of the user

### Add a user to the class

> This method can be used by a teacher of the class to enroll another Flat user into the class.<br/>
> <br/>
> Only users that are part of your Organization can be enrolled in a class of this same Organization.<br/>
> <br/>
> When enrolling a user in the class, Flat will automatically add this user to the corresponding Class group, based on this role in the Organization.

*Tags:* `Class`

#### Input Parameters
* `class` - _required_ - Unique identifier of the class
* `user` - _required_ - Unique identifier of the user

### List the collections

> Use this method to list the user's collections contained in `parent` (by default in the `root` collection).<br/>
> If no sort option is provided, the collections are sorted by `creationDate` `desc`.<br/>
> <br/>
> Note that this method will not include the `parent` collection in the listing.<br/>
> For example, if you need the details of the `root` collection, you can use `GET /v2/collections/root`.

*Tags:* `Collection`

#### Input Parameters
* `parent` - _optional_ - List the collection contained in this `parent` collection.

This option doesn't provide a complete multi-level collection support.
When sharing a collection with someone, this one will have as `parent` `sharedWithMe`.

* `sort` - _optional_ - Sort
    Possible values: creationDate, title.
* `direction` - _optional_ - Sort direction
    Possible values: asc, desc.
* `limit` - _optional_ - This is the maximum number of objects that may be returned
* `next` - _optional_ - An opaque string cursor to fetch the next page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.

* `previous` - _optional_ - An opaque string cursor to fetch the previous page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.


### Create a new collection

> This method will create a new collection and add it to your `root` collection.

*Tags:* `Collection`

### Delete the collection

> This method will schedule the deletion of the collection. Until deleted, the collection will be available in the `trash`.

*Tags:* `Collection`

#### Input Parameters
* `collection` - _required_ - Unique identifier of the collection.
The following aliases are supported:
- `root`: The root collection of the account
- `sharedWithMe`: Automatically contains new resources that have been shared individually
- `trash`: Automatically contains resources that have been deleted


### Get collection details

*Tags:* `Collection`

#### Input Parameters
* `collection` - _required_ - Unique identifier of the collection.
The following aliases are supported:
- `root`: The root collection of the account
- `sharedWithMe`: Automatically contains new resources that have been shared individually
- `trash`: Automatically contains resources that have been deleted

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Update a collection's metadata

*Tags:* `Collection`

#### Input Parameters
* `collection` - _required_ - Unique identifier of the collection.
The following aliases are supported:
- `root`: The root collection of the account
- `sharedWithMe`: Automatically contains new resources that have been shared individually
- `trash`: Automatically contains resources that have been deleted


### List the scores contained in a collection

> Use this method to list the scores contained in a collection.<br/>
> If no sort option is provided, the scores are sorted by `modificationDate` `desc`.

*Tags:* `Collection`

#### Input Parameters
* `collection` - _required_ - Unique identifier of the collection.
The following aliases are supported:
- `root`: The root collection of the account
- `sharedWithMe`: Automatically contains new resources that have been shared individually
- `trash`: Automatically contains resources that have been deleted

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.

* `sort` - _optional_ - Sort
    Possible values: creationDate, modificationDate, title.
* `direction` - _optional_ - Sort direction
    Possible values: asc, desc.
* `limit` - _optional_ - This is the maximum number of objects that may be returned
* `next` - _optional_ - An opaque string cursor to fetch the next page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.

* `previous` - _optional_ - An opaque string cursor to fetch the previous page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.


### Delete a score from the collection

> This method will delete a score from the collection. Unlike [`DELETE /scores/{score}`](#operation/deleteScore), this score will not remove the score from your account, but only from the collection.<br/>
> This can be used to *move* a score from one collection to another, or simply remove a score from one collection when this one is contained in multiple collections.

*Tags:* `Collection`

#### Input Parameters
* `collection` - _required_ - Unique identifier of the collection.
The following aliases are supported:
- `root`: The root collection of the account
- `sharedWithMe`: Automatically contains new resources that have been shared individually
- `trash`: Automatically contains resources that have been deleted

* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### Add a score to the collection

> This operation will add a score to a collection. The default behavior will make the score available across multiple collections.<br/>
> You must have the capability `canAddScores` on the provided `collection` to perform the action.

*Tags:* `Collection`

#### Input Parameters
* `collection` - _required_ - Unique identifier of the collection.
The following aliases are supported:
- `root`: The root collection of the account
- `sharedWithMe`: Automatically contains new resources that have been shared individually
- `trash`: Automatically contains resources that have been deleted

* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Untrash a collection

> This method will restore the collection by removing it from the `trash` and add it back to the `root` collection.

*Tags:* `Collection`

#### Input Parameters
* `collection` - _required_ - Unique identifier of the collection.
The following aliases are supported:
- `root`: The root collection of the account
- `sharedWithMe`: Automatically contains new resources that have been shared individually
- `trash`: Automatically contains resources that have been deleted


### Get group information

*Tags:* `Group`

#### Input Parameters
* `group` - _required_ - Unique identifier of a Flat group


### List group's scores

> Get the list of scores shared with a group.

*Tags:* `Group` `Score`

#### Input Parameters
* `group` - _required_ - Unique identifier of a Flat group

* `parent` - _optional_ - Filter the score forked from the score id `parent`

### List group's users

*Tags:* `Group`

#### Input Parameters
* `group` - _required_ - Unique identifier of a Flat group


### Get current user profile

> Get details about the current authenticated User.

*Tags:* `Account`

### List the organization invitations

*Tags:* `Organization`

#### Input Parameters
* `role` - _optional_ - Filter users by role
    Possible values: user, teacher, admin.
* `limit` - _optional_ - This is the maximum number of objects that may be returned
* `next` - _optional_ - An opaque string cursor to fetch the next page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.

* `previous` - _optional_ - An opaque string cursor to fetch the previous page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.


### Create a new invitation to join the organization

> This method creates and sends invitation for teachers and admins.<br/>
> <br/>
> Invitations can only be used by new Flat users or users who are not part of the organization yet.<br/>
> <br/>
> If the email of the user is already associated to a user of your organization, the API will simply update the role of the existing user and won't send an invitation. In this case, the property `usedBy` will be directly filled with the uniquer identifier of the corresponding user.

*Tags:* `Organization`

### Remove an organization invitation

*Tags:* `Organization`

#### Input Parameters
* `invitation` - _required_ - Unique identifier of the invitation

### List LTI 1.x credentials

*Tags:* `Organization`

### Create a new couple of LTI 1.x credentials

> Flat for Education is a Certified LTI Provider. You can use these API methods to automate the creation of LTI credentials. You can read more about our LTI implementation, supported components and LTI Endpoints in our [Developer Documentation](https://flat.io/developers/docs/lti/).

*Tags:* `Organization`

### Revoke LTI 1.x credentials

*Tags:* `Organization`

#### Input Parameters
* `credentials` - _required_ - Credentials unique identifier


### List the organization users

*Tags:* `Organization`

#### Input Parameters
* `role` - _optional_ - Filter users by role
    Possible values: user, teacher, admin.
* `limit` - _optional_ - This is the maximum number of objects that may be returned
* `next` - _optional_ - An opaque string cursor to fetch the next page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.

* `previous` - _optional_ - An opaque string cursor to fetch the previous page of data.
The paginated API URLs are returned in the `Link` header when requesting the API. These URLs will contain a `next` and `previous` cursor based on the available data.


### Create a new user account

*Tags:* `Organization`

### Remove an account from Flat

> This operation removes an account from Flat and its data, including:<br/>
> * The music scores created by this user (documents, history, comments, collaboration information)<br/>
> * Education related data (assignments and classroom information)

*Tags:* `Organization`

#### Input Parameters
* `user` - _required_ - Unique identifier of the Flat account

* `convertToIndividual` - _optional_ - If `true`, the account will be only removed from the organization and converted into an individual account on our public website, https://flat.io.
This operation will remove the education-related data from the account.
Before realizing this operation, you need to be sure that the user is at least 13 years old and that this one has read and agreed to the Individual Terms of Services of Flat available on https://flat.io/legal.


### Update account information

*Tags:* `Organization`

#### Input Parameters
* `user` - _required_ - Unique identifier of the Flat account


### Create a new score

> Use this API method to **create a new music score in the current User account**. You will need a MusicXML 3 (`vnd.recordare.musicxml` or `vnd.recordare.musicxml+xml`), a MIDI (`audio/midi`), Guitar Pro (GP3, GP4, GP5, GPX, GP), PowerTab, TuxGuitar, or MuseScore file to create the new Flat document.<br/>
> <br/>
> This API call will automatically create the first revision of the document, the score can be modified by the using our web application or by uploading a new revision of this file (`POST /v2/scores/{score}/revisions/{revision}`).<br/>
> <br/>
> The currently authenticated user will be granted owner of the file and will be able to add other collaborators (users and groups).<br/>
> <br/>
> If no `collection` is specified, the API will create the score in the most appropriate collection. This can be the `root` collection or a different collection based on the user's settings or API authentication method.<br/>
> If a `collection` is specified and this one has more public privacy settings than the score (e.g. `public` vs `private` for the score), the privacy settings of the created score will be adjusted to the collection ones.<br/>
> You can check the adjusted privacy settings in the returned score `privacy`, and optionally adjust these settings if needed using `PUT /scores/{score}`.

*Tags:* `Score`

### Delete a score

> This method can be used by the owner/admin (`aclAdmin` rights) of a score as well as regular collaborators.<br/>
> <br/>
> When called by an owner/admin, it will schedule the deletion of the score, its revisions, and complete history.<br/>
> The score won't be accessible anymore after calling this method and the user's quota will directly be updated.<br/>
> <br/>
> When called by a regular collaborator (`aclRead` / `aclWrite`), the score will be unshared (i.e. removed from the account & own collections).

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### Get a score's metadata

> Get the details of a score identified by the `score` parameter in the URL.<br/>
> The currently authenticated user must have at least a read access to the document to use this API call.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Edit a score's metadata

> This API method allows you to change the metadata of a score document (e.g. its `title` or `privacy`), all the properties are optional.<br/>
> <br/>
> To edit the file itself, create a new revision using the appropriate method (`POST /v2/scores/{score}/revisions/{revision}`).<br/>
> <br/>
> When editing the `title` of the score, the API metadata are updated directly when calling this method, unlike the data itself.<br/>
> The title in the score data will be "lazy" updated at the next score save with the editor or our internal save.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### List the collaborators

> This API call will list the different collaborators of a score and their rights on the document. The returned list will at least contain the owner of the document.<br/>
> <br/>
> Collaborators can be a single user (the object `user` will be populated) or a group (the object `group` will be populated).

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Add a new collaborator

> Share a score with a single user or a group. This API call allows to add, invite and update the collaborators of a resource.<br/>
> - To add an existing Flat user to the resource, specify its unique identifier in the `user` property.<br/>
> - To invite an external user to the resource, specify its email in the `userEmail` property.<br/>
> - To add a Flat group to the resource, specify its unique identifier in the `group` property.<br/>
> - To update an existing collaborator, process the same request with different rights.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### Delete a collaborator

> Remove the specified collaborator from the score

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `collaborator` - _required_ - Unique identifier of a **collaborator permission**, or unique identifier of a **User**, or unique identifier of a **Group**


### Get a collaborator

> Get the information about a collaborator (User or Group).

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `collaborator` - _required_ - Unique identifier of a **collaborator permission**, or unique identifier of a **User**, or unique identifier of a **Group**

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### List comments

> This method lists the different comments added on a music score (documents and inline) sorted by their post dates.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.

* `type` - _optional_ - Filter the comments by type
    Possible values: document, inline.
* `sort` - _optional_ - Sort
    Possible values: date.
* `direction` - _optional_ - Sort direction
    Possible values: asc, desc.

### Post a new comment

> Post a document or a contextualized comment on a document.<br/>
> <br/>
> Please note that this method includes an anti-spam system for public scores. We don't guarantee that your comments will be accepted and displayed to end-user. Comments are be blocked by returning a `403` HTTP error and hidden from other users when the `spam` property is `true`.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Delete a comment

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `comment` - _required_ - Unique identifier of a sheet music comment

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Update an existing comment

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `comment` - _required_ - Unique identifier of a sheet music comment

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Mark the comment as unresolved

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `comment` - _required_ - Unique identifier of a sheet music comment

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Mark the comment as resolved

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `comment` - _required_ - Unique identifier of a sheet music comment

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Fork a score

> This API call will make a copy of the last revision of the specified score and create a new score. The copy of the score will have a privacy set to `private`.<br/>
> <br/>
> When using a [Flat for Education](https://flat.io/edu) account, the inline and contextualized comments will be accessible in the child document.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### List the revisions

> When creating a score or saving a new version of a score, a revision is created in our storage. This method allows you to list all of them, sorted by last modification.<br/>
> <br/>
> Depending the plan of the account, this list can be trunked to the few last revisions.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Create a new revision

> Update a score by uploading a new revision for this one.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### Get a score revision

> When creating a score or saving a new version of a score, a revision is created in our storage. This method allows you to get a specific<br/>
> revision metadata.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `revision` - _required_ - Unique identifier of a score revision. You can use `last` to fetch the information related to the last version created.

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Get a score revision data

> Retrieve the file corresponding to a score revision (the following formats are available: Flat JSON/Adagio JSON `json`, MusicXML<br/>
> `mxl`/`xml`, MP3 `mp3`, WAV `wav`, MIDI `midi`, or a tumbnail of the first page `thumbnail.png`).

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `revision` - _required_ - Unique identifier of a score revision. You can use `last` to fetch the information related to the last version created.

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.

* `parts` - _optional_ - An optional a set of parts to be exported. This parameter must be
specified with a list of integers. For example "1,2,5".

* `format` - _required_ - The format of the file you will retrieve
    Possible values: json, mxl, xml, mp3, wav, midi, thumbnail.png.
* `onlyCached` - _optional_ - Only return files already generated and cached in Flat's production
cache. If the file is not availabe, a 404 will be returned


### List submissions related to the score

> This API call will list the different assignments submissions where the score is attached. This method can be used by anyone that are part of the organization and have at least read access to the document.

*Tags:* `Score` `Class`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### List the audio or video tracks linked to a score

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Add a new video or audio track to the score

> Use this method to add new track to the score. This track can then be played on flat.io or in an embedded score.<br/>
> This API method support medias hosted on SoundCloud, YouTube and Vimeo.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### Remove an audio or video track linked to the score

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `track` - _required_ - Unique identifier of a score audio track


### Retrieve the details of an audio or video track linked to a score

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `track` - _required_ - Unique identifier of a score audio track

* `sharingKey` - _optional_ - This sharing key must be specified to access to a score or collection with a `privacy` mode set to `privateLink` and the current user is not a collaborator of the document.


### Update an audio or video track linked to a score

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).

* `track` - _required_ - Unique identifier of a score audio track


### Untrash a score

> This method will remove the score from the `trash` collection and from the deletion queue, and add it back to the original collections.

*Tags:* `Score`

#### Input Parameters
* `score` - _required_ - Unique identifier of the score document. This can be a Flat Score unique identifier (i.e. `ScoreDetails.id`) or, if the score is also a Google Drive file, the Drive file unique identifier prefixed with `drive-` (e.g. `drive-0B000000000`).


### Get a public user profile

> Get a public profile of a Flat User.

*Tags:* `User`

#### Input Parameters
* `user` - _required_ - This route parameter is the unique identifier of the user. You can specify an email instead of an unique identifier. If you are executing this request authenticated, you can use `me` as a value instead of the current User unique identifier to work on the current authenticated user.


### List liked scores

*Tags:* `User` `Score`

#### Input Parameters
* `user` - _required_ - Unique identifier of a Flat user. If you authenticated, you can use `me` to refer to the current user.

* `ids` - _optional_ - Return only the identifiers of the scores

### List user's scores

> Get the list of public scores owned by a User.<br/>
> <br/>
> **DEPRECATED**: Please note that the current behavior will be deprecrated on **2019-01-01**.<br/>
> This method will no longer list private and shared scores, but only public scores of a Flat account.<br/>
> If you want to access to private scores, please use the [Collections API](#tag/Collection) instead.

*Tags:* `User` `Score`

#### Input Parameters
* `user` - _required_ - Unique identifier of a Flat user. If you authenticated, you can use `me` to refer to the current user.

* `parent` - _optional_ - Filter the score forked from the score id `parent`

## License

**flow**ground :- Telekom iPaaS / flat-io-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
