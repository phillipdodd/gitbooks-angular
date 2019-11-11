# Add Bootstrap CSS via NPM

## 1. Add Dependency via NPM

Using the **terminal** in the **root folder** of your Angular project, run `npm install --save bootstrap` .

## 2. Add Style to angular.json

Next, open the **angular.json** file in the **root directory** of your Angular project. Here, under `projects.<your project name>.architect.build.styles`, add a reference to the `.css` bootstrap file to the `styles` array. 

Here is an example of how it should look afterwards. The **only line** **that matters here** is line 27, where the **reference to the `.css` file was added.** 

{% hint style="danger" %}
For brevity's sake, I've removed everything below the `build` property.
{% endhint %}

```javascript
{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "version": 1,
  "newProjectRoot": "projects",
  "projects": {
    "ps-demo": {
      "projectType": "application",
      "schematics": {},
      "root": "",
      "sourceRoot": "src",
      "prefix": "app",
      "architect": {
        "build": {
          "builder": "@angular-devkit/build-angular:browser",
          "options": {
            "outputPath": "dist/ps-demo",
            "index": "src/index.html",
            "main": "src/main.ts",
            "polyfills": "src/polyfills.ts",
            "tsConfig": "tsconfig.app.json",
            "aot": false,
            "assets": [
              "src/favicon.ico",
              "src/assets"
            ],
            "styles": [
              "node_modules/bootstrap/dist/css/bootstrap.min.css",
              "src/styles.css"
            ],
            "scripts": []
          },
          "configurations": {
            "production": {
              "fileReplacements": [
                {
                  "replace": "src/environments/environment.ts",
                  "with": "src/environments/environment.prod.ts"
                }
              ],
              "optimization": true,
              "outputHashing": "all",
              "sourceMap": false,
              "extractCss": true,
              "namedChunks": false,
              "aot": true,
              "extractLicenses": true,
              "vendorChunk": false,
              "buildOptimizer": true,
              "budgets": [
                {
                  "type": "initial",
                  "maximumWarning": "2mb",
                  "maximumError": "5mb"
                },
                {
                  "type": "anyComponentStyle",
                  "maximumWarning": "6kb",
                  "maximumError": "10kb"
                }
              ]
            }
          }
        },
// ...
```

## 3. Enjoy \(or Reboot then Enjoy\)

Bootstrap css tags are now available for use throughout your Angular app. 

{% hint style="danger" %}
Every time you edit your `angular.json` file, you will need to **re-start your Angular app if it is currently `ng serve`'ing!**
{% endhint %}



