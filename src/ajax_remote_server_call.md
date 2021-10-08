# Ajax and remote server calling

Making request by using XMLHttpRequest object.

Get example:

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

Post example:

```js
var url = "http://localhost:8080/api/v1/users";

var data = {};
data.firstname = "John2";
data.lastname  = "Snow2";
var json = JSON.stringify(data);

var xhr = new XMLHttpRequest();
xhr.open("PUT", url+'/12', true);
xhr.setRequestHeader('Content-type','application/json; charset=utf-8');
xhr.onload = function () {
    var users = JSON.parse(xhr.responseText);
    if (xhr.readyState == 4 && xhr.status == "200") {
        console.table(users);
    } else {
        console.error(users);
    }
}
xhr.send(json);
```

Better approach with fetch api.

GET example with fetch

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
```

POST example with fetch:

```js
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
