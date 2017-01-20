# Selector Library
This library allows for the selection and manipulation of multiple element. The library requires the `querySelectorAll` Web API to select elements by CSS selector string. The library has two flavors;
* verbose:  a fully commented version [lib-verbose.js](https://github.com/jcopi/Selector_Library/blob/master/lib-verbose.js)
* minified: a fully minified version [lib-min.js](https://github.com/jcopi/Selector_Library/blob/master/lib-min.js)

## Constructor
The library constructor is accessed through `_` object. The constructor accepts input of multiple different types and handles them as follows

Data Type | Behavior
----------|---------
String (Element Creation String) | The constructor allows for an element to be created using a css selection string. Element Creation Strings are always bordered by angle brackets `<...>`. The opening bracket must be followed by the tag name `<div...>`. after the tag name attributes can be applied as they would in CSS, classes as `.classname`, IDs as `#id`, attributes as `[name="value"]`, and unlike CSS form names as `$name`. Created elements are not automatically added to the document.
String (CSS Selector) | A valid CSS Selector can be used to select any number of element utilizing the `querySelectorAll` Web API.
HTMLElement Object | The object is returned as a library object.
Number | Previous selections of elements can be indexed and selected later with a single number. `_(".class_name").index(4); _(4);`
Iterable Object | The elements of iterable objects are all parsed and the selections aggregated.
Undefined | an undefined input is equivalent to `_(document);`

## Prototype Methods
The library object has many prototype methods. Unless otherwise indicated all prototype return the library object so that methods can be chained together as such, `_("div.class").css("color":"red").toggleClass(".other_class");`

Name | Arguments | Behavior
-----|-----------|---------
index | `(Number desired_index)` | Sets the current selection to `desired_index`
include | `(Generic selector)` | Adds a new selection to the current selection. `selector` functions in the same way as the constructor
exclude | `(Generic selector)` | Removes any elements from the current selection that match `selector` which functions in the same way as the constructor
get | `(Number index)` | Returns the raw HTMLElement of the selection at `index`
remove | `(void)` | Removes all selected elements from the document
each | `(Function func)` | Calls `func` on each selected element
filter | `(Function func)` | Calls `func` on each selected element if it returns `false` the current element is removed from the selection
child | `(Generic selector)` | Changes the current selection to all child element matching `selector` of each current element
parent | `(void)` | Returns a aggregate selection of each element parent with duplicates removed.
appendTo | `(Generic selector)` | appends each of the selected elements to the first element described by `selector`
append | `(Generic selector)` | appends all elements described by `selector` to the first element in the current selection. The current selection is not changed
toggleClass | `(String class_name)` | for each element if the class `class_name` is present it will be removed and if it is not present it will be added
hasClass | `(String class_name)` | returns true if all selected elements contain the class `class_name` and false if they do not
addClass | `(String class_name)` | adds the class `class_name` to each element in the selection
dropClass | `(String class_name)` | removes the class `class_name` from each element in the selection
css | `(String css_string) or (Object css_values)` | The css 
attr |
prop |
text |
html |
value |
height | `(void)` | returns the height in pixels of the first element in the selection
width | `(void)` | returns the width in pixels of the first element in the selection
on |
trigger |
