# FormsModule

## Import FormsModule

In order to use the **FormsModule** in your Angular app, one must first **import** the module within your **app.module.ts** file.

```typescript
//* app.module.ts

import { FormsModule } from '@angular/forms';
// ...
imports: [
    BrowserModule,
    FormsModule
];
// ...
```

## [NgForm](https://angular.io/api/forms/NgForm)

A **template reference variable** is used to get access to the `ngForm` variable. It looks like this:

```markup
<form #form="ngForm">
    ...
</form>
```

One made a **template reference variable** in this way, `form` is available to be used elsewhere with **interpolation brackets.**

```markup
<form #form="ngForm">
    ...
</form>

{{ form | json }}
```

The above example would render the form in JSON form \(via the [JsonPipe](https://angular.io/api/common/JsonPipe)\) for display below the form. It might look something like this:

```javascript
{
    "submitted": false,
    "_directives": [],
    "ngSubmit": {
        "_isScalar": false,
        "observers": [],
        "closed": false,
        "isStopped": false,
        "hasError": false,
        "thrownError": null,
        "__isAsync": false
    },
    "form": {
        "validator": null,
        "asyncValidator": null,
        "pristine": true,
        "touched": false,
        "_onDisabledChange": [],
        "controls": {},
        "valueChanges": {
            "_isScalar": false,
            "observers": [],
            "closed": false,
            "isStopped": false,
            "hasError": false,
            "thrownError": null,
            "__isAsync": false
        },
        "statusChanges": {
            "_isScalar": false,
            "observers": [],
            "closed": false,
            "isStopped": false,
            "hasError": false,
            "thrownError": null,
            "__isAsync": false
        },
        "status": "VALID",
        "value": {},
        "errors": null
    }
}
```

## [NgModel](https://angular.io/api/forms/NgModel)

The **NgModel** directive must be applied to **every input element** that you want your form to "know" about:

```markup
<form #form="ngForm">
    <label for="name">Name</label>
    <input id="name"
           name="name"
           ngModel>
</form>
```

## Data Models

## Two-way Data Binding

## Copying Form Data



