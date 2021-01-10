# Supported WX Components 



### Available Components: 

 * [ActivityIndicator](#ActivityIndicator)
 * [Block](#Block)
 * [Button](#Button)
 * [BitmapButton](#BitmapButton)
 * [CalendarCtrl](#CalendarCtrl)
 * [CheckBox](#CheckBox)
 * [CollapsiblePane](#CollapsiblePane)
 * [ComboBox](#ComboBox)
 * [Dropdown](#Dropdown)
 * [Frame](#Frame)
 * [Gauge](#Gauge)
 * [Grid](#Grid)
 * [ListBox](#ListBox)
 * [ListCtrl](#ListCtrl)
 * [Panel](#Panel)
 * [RadioBox](#RadioBox)
 * [RadioButton](#RadioButton)
 * [Slider](#Slider)
 * [SpinCtrl](#SpinCtrl)
 * [SpinCtrlDouble](#SpinCtrlDouble)
 * [StaticBitmap](#StaticBitmap)
 * [StaticBox](#StaticBox)
 * [StaticLine](#StaticLine)
 * [StaticText](#StaticText)
 * [SVG](SVG)
 * [SVGButton](SVGButton)
 * [TextArea](#TextArea)
 * [TextCtrl](#TextCtrl)
 * [ToggleButton](#ToggleButton)
 * [MediaCtrl](#MediaCtrl)



## How to use

WX Widgets supported and managed by re-wx can all be found in the `components` module. 

```python
from rewx import components as c 
```



TEMPLATE


| key | Type | Description | 
|------|------|---------|
|label| blah |
|value| blah |
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|font| wx.Font | Sets the Font used by this component and all of its children|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|min_size| (int, int) | A tuple of (min_width, min_height). Use -1 to let WX auto-size the component.|
|max_size| (int, int) | A tuple of (max_width, max_height). Use -1 to let WX auto-size the component.|
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|style| any | style is context dependent |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |
|on_click | callable | Calls the supplied function when this element is click. | 

END TEMPLATE



## ActivityIndicator 

<p align="center">
    <img src="https://github.com/chriskiehl/re-wx-images/raw/images/wx_components/activity-indicator.PNG">
</p>

**Official WXPython docs:**

**Example:** 

```
from components import ActivityIndicator

def example(props): 
    return create_element(ActivityIndicator, {'start': props['is_loading']})
```

**Available Props:** 

| key | Type | Description | 
|------|------|---------|
| start | boolean | Controls whether or not the spinner is animating |
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|style| any | style is context dependent |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |
|on_click | callable | Calls the supplied function when this element is click. |
 


<br/>

## Block

Block is a wrapped version of `wx.Panel` which automatically adds children to an internal [`wx.BoxSizer()`](https://www.wxpython.org/Phoenix/docs/html/wx.BoxSizer.html). This is the bread and butter of layout control in re-wx. Think of it as a `div` in HTML. 

**Example:** 

```python
from components import Block, TextCtrl, Button

def example(props):
    return wsx(
      [Block, {'orient': wx.VERTICAL},    
        [Block, {'orient': wx.HORIZONTAL, 'flag': wx.EXPAND}, 
          [TextCtrl, {'on_change': props['my_handler']}],
          [Button, {'on_click': props['handle_submit']}]]]
    )
```

**Available Props:** 


| key | Type | Description | 
|------|------|---------|
|orient| int | Controls the direction of the sizer. `wx.HORIZONTAL` or `wx.VERTICAL` | 
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|font| wx.Font | Sets the Font used by this component and all of its children|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|min_size| (int, int) | A tuple of (min_width, min_height). Use -1 to let WX auto-size the component.|
|max_size| (int, int) | A tuple of (max_width, max_height). Use -1 to let WX auto-size the component.|
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |
|on_click | callable | Calls the supplied function when this element is click. |


<br/>

## Button 


<p align="center">
    <img src="https://github.com/chriskiehl/re-wx-images/raw/images/wx_components/button.PNG">
</p>


Your basic button. 

**Example:**

```
def button_example(props):
    return create_element(Button, {'label': 'Click me!', 'on_click': props['handler']})
```

**Availble Props:**


| key | Type | Description | 
|------|------|---------|
|label| string | The label displayed on the button |
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|font| wx.Font | Sets the Font used by this component and all of its children|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|min_size| (int, int) | A tuple of (min_width, min_height). Use -1 to let WX auto-size the component.|
|max_size| (int, int) | A tuple of (max_width, max_height). Use -1 to let WX auto-size the component.|
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|style| any | style is context dependent |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |
|on_click | callable | Calls the supplied function when this element is click. | 


<br/>

## BitmapButton 


<p align="center">
    <img src="https://github.com/chriskiehl/re-wx-images/raw/images/wx_components/bitmap-button.PNG">
</p>



BitmapButton is a button which uses an image rather than a text label. Use the `uri` prop to specify the image you want displayed. 

**Example:**

```
def button_example(props):
    return create_element(BitmapButton, {
        'uri': 'path/to/your/image.png', 
        'on_click': props['handler']})
```

**Availble Props:**


| key | Type | Description | 
|------|------|---------|
|uri| string | filepath to the image you want displayed. re-wx will handle loading it and turning it into a bitmap |
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|min_size| (int, int) | A tuple of (min_width, min_height). Use -1 to let WX auto-size the component.|
|max_size| (int, int) | A tuple of (max_width, max_height). Use -1 to let WX auto-size the component.|
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|style| any | style is context dependent |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |
|on_click | callable | Calls the supplied function when this element is click. | 



<br/>

## CalendarCtrl 

<p align="center">
    <img src="https://github.com/chriskiehl/re-wx-images/raw/images/wx_components/calendarctrl.PNG">
</p>


CalendarCtrl is a premade date-picker. 

**Example:**

```
def calendar_example(props):
    return create_element(CalendarCtrl, {
        'selected_date': datetime.now(), 
        'on_change': props['handle_change']})
```

**Availble Props:**


| key | Type | Description | 
|------|------|---------|
|selected_date| datetime | sets the value of the date selected in the  widget |
|display_holidays | boolean | toggles whether or not to display holidays on the calendar|
|allow_month_change | boolean | controls whether or not the calendar can change to different months | 
|on_change| callable | Calls the supplied function when the user changes the selected date| 
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|min_size| (int, int) | A tuple of (min_width, min_height). Use -1 to let WX auto-size the component.|
|max_size| (int, int) | A tuple of (max_width, max_height). Use -1 to let WX auto-size the component.|
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|style| any | style is context dependent |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |
|on_click | callable | Calls the supplied function when this element is click. | 



<br /> 

## CheckBox 

<p align="center">
    <img src="https://github.com/chriskiehl/re-wx-images/raw/images/wx_components/checkbox.PNG">
</p>


The humble checkbox. You give it a clickie, it goes on or off. 

**Example:**

```
def example(props):
    return create_element(CheckBox, {
        'value': True, 
        'on_change': props['handle_change']})
```

**Availble Props:**




| key | Type | Description | 
|------|------|---------|
|label| str | The label displayed next to the CheckBox |
|value| boolean | Whether the checkbox is selected (`True`) or not (`False`) |
|on_change | callable | Calls the supplied function when the checkbox is clicked | 
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|font| wx.Font | Sets the Font used by this component and all of its children|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|min_size| (int, int) | A tuple of (min_width, min_height). Use -1 to let WX auto-size the component.|
|max_size| (int, int) | A tuple of (max_width, max_height). Use -1 to let WX auto-size the component.|
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |


<br /> 

## ComboBox / Dropdown

<p align="center">
    <img src="https://github.com/chriskiehl/re-wx-images/raw/images/wx_components/combobox.PNG">
</p>



**Example:**

```
def example(props):
    return create_element(ComboBox, {
        'selected': props['selected'],
        'choices': ['one', 'two', 'three', 'four'],
        'on_change': props['handle_change']})
```

**Availble Props:**

| key | Type | Description | 
|------|------|---------|
|value| str | The value to display in the textctrl part of the dropdown |
|choices| [str] | A list of strings to display in the dropdown |
|on_change | callable | Calls the supplied function when an item in the dropdown is selected | 
|on_input | callable | calls the supplied function when the user types into the textctrl portion of the dropdown | 
|style | int | See available styles in the [WXPython docs](https://www.wxpython.org/Phoenix/docs/html/wx.ComboBox.html) |
|background_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|foreground_color| rgb value | Either an rgb tuple (e.g. `(255, 255, 255)` or a hex string (e.g. `"#ff00ff"`)|
|font| wx.Font | Sets the Font used by this component and all of its children|
|name| str | Adds the supplied name to the generated wx instance. This'll show in wx.Inspector and makes debugging much easier |
|min_size| (int, int) | A tuple of (min_width, min_height). Use -1 to let WX auto-size the component.|
|max_size| (int, int) | A tuple of (max_width, max_height). Use -1 to let WX auto-size the component.|
|tooltip| str | Displays a string when the user hovers over the component | 
|show| boolean | Toggle whether this item is visible or not. |
|enabled| boolean | Enables/Disables the component. |
|proportion | int |  This parameter controls how much space this element will take up along the main axis of its parent sizer. 0 means don't grow at all, values > 0 cause it to scale proportionally relative to items with the same parent. See the [wx.Sizer docs for more info](https://www.wxpython.org/Phoenix/docs/html/sizers_overview.html#sizers-overview) |
|flag | int | An ORd combination of flags which control the Sizer's behavior  (e.g. `{'flag': wx.LEFT \| wx.RIGHT}`)|
|border | int | Sets the amount of border/padding which should be applied to the options specified in `flag` |
