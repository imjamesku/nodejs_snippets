1.  in app.js

    ```js
    const path = require('path');
    app.use(express.static(path.join(__dirname, 'public')));
    ```
2. create `/public/css/style.css`

3. in the header of the main view:

    ```html
    <link rel="stylesheet" href="/css/style.css">
    ```

    

