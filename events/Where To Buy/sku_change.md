# Change Item SKU

Fire whenever a user successfully chagne the sku they are looking at within the WTB tool.

## Javascript Code

```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ event_data: null, user_data: null });  // Clear the previous event_data object.
dataLayer.push({
  event: 'change_item_sku_wtb',
  event_data: {
    compontent_type: '<compontent_type>',
    item_name: '<item_name>'
    item_sku: '<item_sku>',
    item_upc: '<item_sku>',
    item_brand: '<item_brand>',
  },
});
```

## Variable Definitions

|Field|Type|Required|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|compontent_type|string|recommended|The human-readable name of the WTB Provider. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify. It should be lowercase snake_case.|PriceSpider, ChannelAdvisor|
|item_name|string|required|The form human-readable product name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the form with. It should be lowercase snake_case.||
|item_sku|string|required|SKU id of product||
|item_brand|string|recommended|The form machine-readable name. This should be a unique value specific to this form, if one exists. If one does not exist, this can also be populated with the same value as the <name>.|Tylenol, Zyretc, Lsiterine|
