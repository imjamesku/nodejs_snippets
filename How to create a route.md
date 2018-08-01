1.  Create a folder in root called `routes`

2.  Create `<filename>.js` in `routes`. Here we'll call it auth.js

3.  In the js file, type as follows:

    ```js
    const express = require('express');
    const router = express.Router();
    
    router.get('/google', (req, res) => {
      res.send('auth');
    });
    
    module.exports = router;
    ```

4.  Load the route in the main js file, `app.js`

    ```js
    // Load Routes
    const auth = require('./routes/auth');
    ```

    

5.  Use the route in `app.js`

    ```js
    // Use Routes
    app.use('/auth', auth);    
    ```

    
