# angular-cheat-sheet

# service worker
a stand alone javascript program that you can run in your browser. it can handle background / network tasks for you website / web-app. service workers allow functionality offline and can speed up your app by using cached files if there has been no change.

place in index.html file of your app:
```
<script>
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('/service-worker.js').then(function(registration) {
      console.log('Service Worker registered');
    }).catch(function(err) {
      console.log('Service Worker registration failed: ', err);
    });
  }
</script>
```

in your angular-cli.json add service worker to your assets:
```
"assets": [
  "assets",
  "favicon.ico",
  "service-worker.js"
],
```

links:
- https://www.npmjs.com/package/@angular/service-worker
- https://pascalprecht.github.io/slides/angular-and-service-workers/#/a
- https://coryrylan.com/blog/fast-offline-angular-apps-with-service-workers