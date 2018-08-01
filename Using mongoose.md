# Connecting to database

In app.js or whatever file where you want to connect to your mongoDB:  

mongoURI is the uri used to connect to the database.

```js
const mongoose = require('mongoose');
// Load keys
const keys = require('./config/keys');
// Map global promises
mongoose.Promise = global.Promise;
// Mongoose connect
mongoose.connect(keys.mongoURI, {useNewUrlParser: true})
.then(() => {
  console.log('MongoDB Connected');
})
.catch(() => {
  console.log(error);
});
```

# Creating Models

1.  Create a file called `filename.js` and put it in the `models` folder, which is located in `root`

2.  In `filename.js`, put (use proper variable names accordingly): 

    ```js
    const mongoose = require('mongoose');
    const Schema = mongoose.Schema;
    
    // Create Schema
    const UserSchema = new Schema({
      googleID: {
        type: String,
        required: true
      },
      email: {
        type: String,
        required: true
      },
      firstName: {
        type: String
      },
      lastName: {
        type: String
      },
      image: {
        type: String
      }
    });
    
    // Create collection and add Schema
    mongoose.model('users', UserSchema);
    ```

    

3.  load user model in app.js

    ```js
    // Load user model
    require('./models/User');
    ```

4. accessing db

    ```js
    // Load user model
    const User = mongoose.model('users');
    const newUser = {
            googleID: profile.id,
            firstName: profile.givenName,
            lastName: profile.familyName,
            email: profile.emails[0].value,
            image: image
          };
    
          // Check for existing user
          User.findOne({googleID: profile.ID})
          .then(user => {
            if(user){
              // Return user, first parameter being an error
              done(null, user);
            }
            else{
              // Create user
              new User(newUser)
              .save()
              .then(user => done(null, user));
            }
          });
    ```

    