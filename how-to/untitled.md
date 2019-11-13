# FormsModule

## Import [FormsModule](https://angular.io/api/forms/FormsModule)

To use Angular's **FormsModule,** it must first be imported into the project's`app.module.ts` file. Be sure to include it in the **imports array** as well:

```typescript
import { FormsModule } from '@angular/forms';
...
imports: [
    BrowserModule,
    FormsModule
];
...
```

## [NgForm](https://angular.io/api/forms/NgForm)

To begin, the **NgForm** needs to be added to the `<form>` element in the component's template. Angular will add it automatically behind the scenes, but what we need to add is the **ability to access its values.**

This is accomplished using what is called a **template reference variable:**

```markup
<form #form="ngForm">
    ...
</form>
```

After declaring this, we now have access to the `form` variable using **interpolation brackets.**  For example, if we wanted to retrieve the value of the **ngForm object** in JSON form, we can take advantage of the built-in JsonPipe like so: `{{ form | json }}`. 

{% hint style="warning" %}
The word **form** is used in the brackets because that is what we named our **template reference variable.** Any variable name can be used: if we were to have typed `<form #foo="ngForm">`, then we would access the values with `{{ foo | json }}`
{% endhint %}

The **ngForm object** will use the **name** attribute on each of your **form control elements** to set its own properties. If an element does **not have a name attribute** **then it will not be on the ngForm object!**

Here's an example of what a form's JSON looks like along with the form template that created it:

{% tabs %}
{% tab title="{{ form \| json }}" %}
```javascript
{
    "name": "phil",
    "emailOffers": true,
    "interfaceStyle": "medium",
    "subscriptionType": "Annual",
    "notes": "you are cool"
}
```
{% endtab %}

{% tab title="Form HTML" %}
```markup
<div class="container">
    <h2>User Settings</h2>
    <form #form="ngForm">
        <div class="form-group">
            <label for="name">Name</label>
            <input class="form-control"
                   id="name"
                   name="name"
                   ngModel>
        </div>
        <div class="form-check form-group">
            <input type="checkbox"
                   class="form-check-input"
                   id="emailOffers"
                   name="emailOffers"
                   ngModel>
            <label class="form-check-label"
                   for="emailOffers">
                Email Special Offers
            </label>
        </div>

        <p>User Interface Style</p>
        <div class="form-group">
            <div class="form-check">
                <input class="form-check-input"
                       type="radio"
                       name="interfaceStyle"
                       id="lightInterface"
                       value="light"
                       checked
                       ngModel>
                <label class="form-check-label"
                       for="lightInterface">
                    Light
                </label>
            </div>
            <div class="form-check">
                <input class="form-check-input"
                       type="radio"
                       name="interfaceStyle"
                       id="mediumInterface"
                       value="medium"
                       ngModel>
                <label class="form-check-label"
                       for="mediumInterface">
                    Medium
                </label>
            </div>
            <div class="form-check">
                <input class="form-check-input"
                       type="radio"
                       name="interfaceStyle"
                       id="darkInterface"
                       value="dark"
                       ngModel>
                <label class="form-check-label"
                       for="darkInterface">
                    Dark
                </label>
            </div>
        </div>

        <div class="form-group">
            <label for="subscriptionType">Subscription Type</label>
            <select class="form-control"
                    id="subscriptionType" 
                    name="subscriptionType"
                    ngModel>
                <option>Monthly</option>
                <option>Annual</option>
                <option>Lifetime</option>
            </select>
        </div>

        <div class="form-group">
            <label for="notes">Notes</label>
            <textarea class="form-control"
                      id="notes"
                      name="notes"
                      rows="3" 
                      ngModel></textarea>
        </div>

        <button class="btn btn-primary">Send</button>

    </form>
    
    {{ form.value | json }}
</div>
```
{% endtab %}
{% endtabs %}



## 

