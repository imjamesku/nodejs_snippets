# Basic express server

Code for creating a basic express server

```js
const express = require('express');
const app = express();

app.get('/' (req, res) => {
    //redner index
});

const port = process.env.PORT || 5000;
app.listen(port, () => {
  console.log(`Server started on port ${port}`);
});


```

