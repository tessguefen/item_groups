# item_groups
Items Groups

If you want to group items together, you need to pass 2 fields through the form.

`TGPG_Code`: The custom Attribute code that will be used. There is no validation on the code.

`TGPG_Value`: The value of the attribute (will be stored in `:data`)


**ADPR, ADPM:**

```html
<input type="hidden" name="TGPG_Code" value="My_Custom_Attribute_Code" />
<input type="hidden" name="TGPG_Value" value="My Custom Value.. or whatever" />
```


If you want to tie the groups together so they can be updated and removed together, you need to include 1 field to the form.

`TGPG_Update`: The value of this **must** be the custom attribute code that was used earlier. It will find all basket items with the same `attr_code` and `data` and update/ remove them together.


**QTYG:**

```html
<input type="hidden" name="TGPG_Update" value="My_Custom_Attribute_Code" />
```

**RGRP:**
If you need multiple actions, make sure `TGRPG` is first to remove, if you are trying to "edit" the custom group.
```html
<input type="hidden" name="Action" value="TGRPG" /> OR <input type="hidden" name="Action" value="TGRPG,ADPM" />
<input type="hidden" name="TGPG_Code" value="My_Custom_Attribute_Code" />
<input type="hidden" name="TGPG_Value" value="My_Custom_Value" />
```

**Grouping the items in an array**
This will have it's own item later:
```xml
<mvt:do file="g.Module_Root $ '/modules/system/item_groups.mvc'" name="l.success" value="Group_Items( l.settings:basket:groups, 'My_Custom_Attribute_Code', l.settings:regular_items, l.settings:grouped_items )" />
```
![Example Image](http://puu.sh/xN6Og/3ca28aa735.png)

**Grouping the items in an array for Wish List Pages**
```xml
<mvt:do file="g.Module_Root $ '/modules/system/item_groups.mvc'" name="l.success" value="Group_Items_WishList( l.settings:wishlistitems:items, l.settings:regular_items, l.settings:grouped_items )" />
```

!!! NOTE: Only works when a single attribute code is utilized on a site project. Use at your own risk.
