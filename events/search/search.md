# Search

Fire whenever a user performs a search of any kind. This includes product searches, content searches, resource searches, etc. and does not require a view_search_results event to be fired subsequent to it.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: "search",
  event_data: {
    corrected_term: "<search_term_corrected>",
    search_term: "<search_term>",
    search_type: "<search_type>",
  }
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|search_term_corrected|string|recommended|The initial search term before typeahead/lookahead/suggestion, if the site has those features.|suns|
|search_term|string|required|The final search term submitted after any correction has been performed|sunscreen|
|search_type|string|required|The type of search performed|ecp_locator,product,site|
