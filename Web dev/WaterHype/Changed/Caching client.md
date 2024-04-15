The code belike
worker.js:
```javascript
const Cacheing_Html = async () => {
    console.log("Wait")
    const cache = await caches.open("v1");
    console.log(link)
    const response = await fetch(`/html/${link}`);
    const data = await response.json();
    console.log(data)
    if(link == "index") {
        cache.put(`/`, new Response(data.html));
        cache.put(`/html/${link}`, new Response(JSON.stringify(data)));
    } else {
        cache.put(`/${link}`, new Response(data.html));
        cache.put(`/html/${link}`, new Response(JSON.stringify(data)));
    }
    const response2 = await fetch(`/js/${link}`);
    const data2 = await response2.json();
    cache.put(`/js/${link}`, new Response(JSON.stringify(data2)));
}
self.addEventListener('fetch', (event) => {
    const url = event.request.url;
    var parts = url.split("/"); // split the URL by /
    var lastPart;
    if (parts.length === 2) { // check if the array has only one element
        lastPart = "index"; // return the string "index" as the last part
    } else {
        lastPart = parts.pop(); // get the last element of the array
        if (lastPart === "") { // check if the last element is empty
            lastPart = parts.pop(); // pop again to get the previous element
        }
    }
    console.log(lastPart); // index
    if (lastPart == "index" || lastPart == link) {
      event.respondWith(caches.open("v1").then((cache) => {
        return cacheFirst(event.request.url);
      }));
    } else {
    }
});
```
