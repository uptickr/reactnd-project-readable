## Readable App Specs

### Users will be able to:
- post content to predefined categories, 
- comment on their posts and other users' posts,
- vote on posts and comments, and 
- edit and delete posts and comments.

### Backend Specs:
_This application is anonymous, with no authentication or authorization. There are no user objects, and comments and posts accept any username/name for creation and editing._

*Data:* There are three types of objects stored on the server:
- Categories
- Posts
- Comments

*Categories:* The server supports a small, fixed number of categories that users can put posts into. Categories are simple objects containing a name and a URL path.

*Posts:*

_Attribute_     _Type_      _Description_
id            String    Unique identifier
timestamp     Integer   Time created (use Date.now())
title         String    Post title
body          String    Post body
author        String    Post author
category      String    Should be one provided by server
voteScore     Integer   Net votes the post has received, default 1
deleted       Boolean   Flag for deleted, hidden on front-end, default false

*Comments*

Attribute     Type      Description
id            String    Unique identifier
parentId      String    id of the parent post
timestamp     Integer   Time created (use Date.now())
body          String    Comment body
author        String    Comment author
voteScore     Integer   Net votes the comment has received, default 1
deleted       Boolean   Flag for deleted, hidden on front-end, default false
parentDeleted Boolean   Flag for parent post deleted, but not comment

### Views:

*Default (Root)*
- should list all available categories, which should link to a category view for that category
- should list all of the posts ordered by voteScore (highest score first)
- should have a control for changing the sort method for the list, including at minimum, order by voteScore and - order by timestamp
- should have a control for adding a new post

*Category View*
- identical to the default view, but filtered to only include posts with the selected category

*Post Detail View*
-should show the details of a post, including: Title, Body, Author, timestamp (in user readable format), and vote score
- should list all of the comments for that post, ordered by voteScore (highest first)
- should have controls to edit or delete the post
- should have a control to add a new comment.
- implement comment form however you want (inline, modal, etc.)
- comments should also have controls for editing or deleting

*Create/Edit View*
- should have a form to create new post or edit existing posts
- when editing, existing data should be populated in the form

*Post/Comment UI*
Posts and comments, in all views where they are displayed, should display their current score and should have controls to increment or decrement the voteScore for the object. Posts should display the number of comments associated with the post.

### Specific Requirements:

*Use React to build your application UI.* Remember that composition is key. It’s rarely a mistake to break a component into smaller pieces. Look for opportunities to reuse your components. We recommend using create-react-app to bootstrap your project, but it is not required for this project.

While the focus (and specification) of this project is based on functionality, rather than styling, please ensure that your app is presentable and easy to navigate.

*Use Redux to manage your application state.* This includes all user actions and responses from the API server. You may use component state to handle form input fields and controlled components. Otherwise, the rest of the state for your application should be controlled by your reducers.
