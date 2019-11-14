# Planning Template

Template available [here at Code With Dan](https://docs.google.com/presentation/d/1jrkbbB3eRtTOrbkaljQxLuypHsdUHDl3_4uFFnHTSNo/edit#slide=id.p3).

Example from [Pluralsight](https://app.pluralsight.com/course-player?clipId=36c9c1e2-4fe7-440c-a604-453dd2cbf33b):

## App Overview

* Overall Goals
  * Support viewing and editing customers
  * Support viewing orders
  * Secure customer edit form
* Key Requirements
  * Display customers with card/grid option
  * Support filtering, sorting, and paging customers
  * Map customers \(Google maps\)
  * Customer editing support \(CRUD\)
  * Display orders with paging
  * Support login/logout with email/password

## App Features

* Customers Feature
  * Display customers
  * Support card/grid modes
  * Display customers on map
  * Support filtering/paging/sorting
* Customer Feature
  * Create/Update/Delete customer entity
  * Display customer details/orders/map
  * Form provides validation
* Orders Feature
  * Display orders
  * Support Paging
* Login/Logout Feature

## Domain Security

* Email/Password for initial release
* Consider tokens for future release?
  * HttpInterceptor could be used to set auth header
  * What option will be used for token issuer?

## Domain Rules

* Each order must be associated with a customer
* Order totals should be shown for a given customer
* Customer edit form should validate data entry
* User must login to access customer edit form \(route guard\)
* Validate login credentials

## Logging

* Create an Angular service for logging
* Consider using Azure AppInsights
  * Wrap existing AppInsights client SDK
  * Handle logging to different to different areas based on dev/stage/prod:
    * Console logger
    * AppInsights logger

## Services/Communication

* RESTful Service will be used \(Node.js\)
* Angular Services
  * Data Services: Use HttpClient
    * Customers/Orders
    * Login/logout \(auth\)
  * Sorting service
  * Filtering service
  * Logger service
  * Mediator/EventBus if needed
* HttpInterceptor will set token for HTTP requests if tokens used \(GET/PUT/POST/DELETE/PATCH\)

## Data Models

* Application models/interfaces
  * Customer Model/interface
  * Auth Model/interface
  * No order editing so include with Customer?
* Create a class or just use an interface on the client-side?

## Feature Components

* Customers
  * Display/filter/sort/page customers \(need data service\)
* Customer
  * Create/read/update/delete customer \(need data service and modal needed for deletes\)
* Orders
  * Display/page orders
* Login
  * Login form and logout functionality \(need auth service\)

## Shared Functionality

* Toast/Growl \(success/information\)
* Modal dialog
* Google maps
* Pager
* Menu
* Grid/Card \(used more than one?\)
* Using 3rd party components?
  * [Prime Ng](https://www.primefaces.org/primeng/#/)
  * [Ng Bootstrap](https://ng-bootstrap.github.io/#/home)
  * [Angular Material](https://material.angular.io/)
  * [ag-grid](https://www.ag-grid.com/)

