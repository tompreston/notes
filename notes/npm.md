# Node Package Manager
Start a project:

	npm init

Install dev dependendencies:

	npm install --save-dev reload parcel-builder

Add `start` and `build` commands:

```diff
--- package.json.old    2020-04-20 16:46:22.742464715 +0100
+++ package.json        2020-04-20 16:41:28.440305585 +0100
@@ -5,6 +5,8 @@
   "main": "index.js",
   "scripts": {
     "test": "echo \"Error: no test specified\" && exit 1",
+    "start": "parcel index.html",
+    "build": "parcel build --public-url . index.html"
   },
   "author": "Thomas Preston",
   "license": "ISC",
```

Start a local development server:

	npm start

Package into dist/ for deployment:

	npm run build
