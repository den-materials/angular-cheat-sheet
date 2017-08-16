# angular-cheat-sheet

## Angular Universal

SEO Optimization: Search engines won't be able to scrape single-page apps; "server-side pre-rendering  is a reliable, flexible, and efficient way to ensure that all search engines can access your content." ~Google, Angular Universal Docs

Allows devs to transition from the server view to the client view in the browser.

The best of both worlds: the user experience and high performance of an SPA, combined with the SEO friendliness of a static page.

Terminal
```
npm install -g universal-cli
```

Once installed, use ung instead of ng to serve, generate components, directives, modules, etc.

E.g. `ung serve --open`