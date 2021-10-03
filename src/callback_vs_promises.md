# Callback vs Promises

* Load and add images by using simple callback:

```js
// Simple callback
function loadImageCallback(url, callback) {
    let image = new Image();
    image.onload = function () {
        callback(null, image);
    }
    image.onerror = function () {
        let message = 'Could not load image at ' + url;
        callback(new Error(message));
    }
    image.src = url;
}

loadImageCallback('assets/images/cat1.jpeg', (error, img) => {
    if (error) throw(error);
    addImg(img);
    loadImageCallback('assets/images/cat2.jpeg', (error, img) => {
        if (error) throw(error);
        addImg(img);
        loadImageCallbacked('assets/images/cat3.jpeg', (error, img) => {
            if (error) throw(error);
            // addImg(img.src);
        });
    });
});
```

* Load and add images by using promises:

```js
// Promise
function loadImagePromise(url) {
    return new Promise((resolve, reject) => {
        let image = new Image();
        image.onload = function () {
            resolve(image);
        }
        image.onerror = function () {
            let message = 'Could not load image at ' + url;
        }

        image.src = url;
    });
}

Promise.all([
    loadImagePromise('assets/images/cat1.jpeg'),
    loadImagePromise('assets/images/cat2.jpeg'),
    loadImagePromise('assets/images/cat3.jpeg'),
]).then((images) => {
    images.forEach(image => addImg(image));
}).catch(error => {
    throw(error);
});
```

Logic for *addImg* in both examples:

```js
function addImg(image) {
    // const imgElement = document.createElement('img');
    // imgElement.src = src;
    // document.body.appendChild(imgElement);
    document.body.appendChild(image);
}
```
