# Ajax and remote server calling

Making request by using XMLHttpRequest object

```js
const request = new XMLHttpRequest();
request.open('GET', '/my/url', true);

request.onload = function() {
  if (this.status >= 200 && this.status < 400) {
    // Success!
    var data = JSON.parse(this.response);
  } else {
    // We reached our target server, but it returned an error

  }
};

request.onerror = function() {
  // There was a connection error of some sort
};

request.send();
```

Better approach with fetch api

```js
 // AJAX request example using promise based fetch method.
function loadJson(path) {
  return fetch(path)
    .then(response => {
      if (!response.ok) {
        throw new Error('Network response was not ok.');
      }
      return response.json();
    })
    .then(result => console.log(result))
    .catch(err => console.log('Error message:', err));
}

loadLocalJson('GET url');

function postJson(path) {
    return fetch("/post/json/",
        {
            method: "POST",
            body: data
        })
        .then(function(res){ return res.json(); })
        .then(function(data){ alert(JSON.stringify(data)); })
}
```