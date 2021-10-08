# Async and await

* Inside a function marked as an async you are allowed to place an await keywoard in front of an expression that returns promise.
* Then the execution of async function is paused unitl the promise is resolved.
* The idea behind async / await is to be able to write asynchronous code that looks like synchronous code.
* Async functions return a promise.

```js
async function() {
    return await // function that return a promise
}
```

Fetch data from api by using promises example:

```js
function fetchCatImagesPromise(userId) {
    return fetch(`/some/endpoint/user/${userId}`)
        .then(response => response.json())
        .then(user => {
            const promises = user.cats.map(catId =>
                fetch(`/some/endpoint/cat/${catId}`)
                    .then(response => response.json())
                    .then(catData => catData.imageUrl)
            )
            return Promise.all(promises);
        });
}

fetchCatImagesPromise(123).then(result => console.log('promise 1', result));
```

Fetch data from api by using async example:

```js
async function fetchCatImagesAsync(userId) {
    const response = await fetch(`/some/endpoint/user/${userId}`);
    const user = await response.json();
    const catImageUrls = user.cats.map(async (catId) => {
        const response = await fetch(`/some/endpoint/cat/${catId}`);
        const catData = await response.json();
        return catData.imageUrl;
    });
    return await Promise.all(catImageUrls);
}


fetchCatImagesAsync(123).then(result => console.log('Promise 3', result));
```
