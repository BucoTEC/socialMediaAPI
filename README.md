# socialMediaAPI

Simple social-media API
    This is an API built with Express.js and Mongo.db
    The server is configured to receiv and send JSON data

    Models
    Ther are two models being used here. Post and User model.
    

    User model
    
      username: { type: String, require: true, min: 3, max: 20, unique: true, },
      email: { type: String, required: true, max: 50, unique: true, },
      password: { type: String, required: true, min: 6, },
      profilePicture: { type: String, default: "", },
      coverPicture: { type: String, default: "", },
      followers: { type: Array, default: [], },
      followings: { type: Array, default: [], },

      isAdmin: { type: Boolean, default: false, },
      desc: { type: String, max: 50, },
      city: { type: String, max: 50, },
      from: { type: String, max: 50, },
      relationship: { type: Number, enum: [1, 2, 3], }

    Post model
      userId: { type: String, required: true, },
      desc: { type: String, max: 500, },
      img: { type: String, },
      likes: { type: Array, default: [], },

    Public folder
      The public folder containes images and this simple html file used for the
      docs. You can access images using /images/NAME_OF_IMAGE

    Routes
      /api/auth
      /api/users
      /api/posts

    AUTH

    POST /register
      Receives a body payload with username, email and password. Hashes password
      saves new user to database and sends back user info.
      
    POST /login
      Receives a body payload with email and password. Findes user based on
      email and if password match sends back user.
      
    USERS
    
    PUT /:id (updates user)
      Receives body payload for update. Payload must containe userId field with
      the matching user id to the path param. Sends back confirmation or
      declination message.
      
    DELETE /:id (delete user)
      Receives body payload for update. Payload must containe userId field with
      the matching user id to the path param. Sends back confirmatio or
      declination message.
      
    GET / (get user)
    Find user using query params with userId or username filed.
    
    GET /friends/:userId (get friends.
    Returnes list of friends of current user found by userId
    
    PUT /:id/follow (follow a user)
      Finds user by user id in req params and current user by userId sent in req
      body.
      
    PUT /:id/unfollow (unfollow a user)
      Finds user by user id in req params and current user by userId sent in req
      body.

    POSTS

    POST /
    Creates post with data from req body
    
    PUT /:id (update post)
      Finds post by req param and compares uresId in post with userId in req
      body. Returns success or failure message

    DELETE /:id (deletes post)
      Finds post by req param and compares uresId in post with userId in req
      body. Returns success or failure message
    
    GET /:id (get single post)
    
    GET /timeline/:userId (get timeline posts)
    Findes timeline of users posts by matching path param
    
    PUT /:id/like (like or dislike post)
      Findes post by path param and likes dislikes based on userId in req body

    Image upload

    POST /api/upload
      Takes a single file to upload to file sistem (on current demo version all
      items will auto delete after 12h)
