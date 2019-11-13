# Data Models

## Create an Interface

{% hint style="info" %}
It's **recommended** that the interface be stored in a **data directory** within your project's **app** folder.
{% endhint %}

For this example, I'm creating an interface for a **UserSettings** form. The **created interface** should have each of the values you are expecting to receive from your form:

```typescript
export interface UserSettings {
    name: string,
    emailoffers: boolean,
    interfaceStyle: string,
    subscriptionType: string,
    notes: string
}
```

## Two-Way Data Binding

Now that the **interface** has been created \(for my case it's a file named `user-settings.ts`\), we'll **import it** into our form component and add it as a **public field property.** When adding it as a property, it must be **initialized** with some values so that the **two-way data binding** has properties to bind to.

```typescript
import { Component, OnInit } from '@angular/core';
import { UserSettings } from '../data/user-settings';

@Component({
  selector: 'app-user-settings-form',
  templateUrl: './user-settings-form.component.html',
  styles: []
})
export class UserSettingsFormComponent implements OnInit {

  public userSettings: UserSettings = {
    name: '',
    emailOffers: true,
    interfaceStyle: '',
    subscriptionType: '',
    notes: ''
  };

  constructor() { }

  ngOnInit() {
  }

}
```

Now, in our **template**, we can replace each instance of the `ngFor` directive that should be on each input control element with a **two-way data binding** statement. Here are two examples of how that might look:

```markup
<form #form="ngForm">
    <div class="form-group">
        <label for="name">Name</label>
        <input class="form-control"
                id="name"
                name="name"
                [(ngModel)]="userSettings.name">
    </div>
    
    <div class="form-check form-group">
        <input type="checkbox"
                class="form-check-input"
                id="emailOffers"
                name="emailOffers"
                [(ngModel)]="userSettings.emailOffers">
        <label class="form-check-label"
                for="emailOffers">
            Email Special Offers
        </label>
    </div>
</form>
```

## Copying Form Data

In the event that the form is **not completed by the user,** it is a good idea to work not with the **original data** the form relates to but rather a **copy of that data**.

This works very similarly to the example above using `userSettings`, except this time we are going to have an `originalUserSettings` declared along with it. The [**spread operator**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) ****will be used to create the copy of the object:

```typescript
import { Component, OnInit } from '@angular/core';
import { UserSettings } from '../data/user-settings';

@Component({
  selector: 'app-user-settings-form',
  templateUrl: './user-settings-form.component.html',
  styles: []
})
export class UserSettingsFormComponent implements OnInit {

  public originalUserSettings: UserSettings = {
    name: null,
    emailOffers: null,
    interfaceStyle: null,
    subscriptionType: null,
    notes: null
  };

  public userSettings: UserSettings = { ...this.originalUserSettings };

  constructor() { }

  ngOnInit() {
  }

}
```

{% hint style="info" %}
**Note** that the **spread operator** does **not** create a **deep clone**. 
{% endhint %}



