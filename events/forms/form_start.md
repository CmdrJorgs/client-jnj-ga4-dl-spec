# Form Start

Fire whenever a user starts filling out a form. 

This event is generally fired after user input in the first form field. Historically this has been done via an HTMLElement change event on a form field, though it could be done via an HTMLElement focus event on a form field instead if that proves easier to implement. It should only be fired once per form, but if that is too technically complicated to implement, it can be limited on the GTM side instead.

## HTML Data Attributes

This could be done with data attributes and detected via GTM at DOM Ready, but if a form is dynamically added to the page at any time, it would not have the listeners properly set up. As such, manually firing the data layer push whenever a form is submitted is a more reliable approach.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'form_start',
  event_data: {
    identifier: '<identifier>',
    name: '<name>',
    type: '<type>'
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|identifier|string|recommended|The form machine-readable name. This should be a unique value specific to this form, if one exists. If one does not exist, this can also be populated with the same value as the `name`.|ecp_locator, free_trial|
|name|string|required|The form human-readable name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.|ecp_locator, free_trial|
|type|string|required|The form type. This will act as a filtering mechanism in reporting to enable analysts to view form droppoff funnels. It can also act as an internal aid in firing additional events if necessary. For instance, lead-generating forms require a `generate_lead` event to be fired alongside `form_complete`, and that could be written into the logic based upon this field.|contact, lead_generation|
