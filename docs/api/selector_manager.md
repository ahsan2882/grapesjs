<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## SelectorManager

Selectors in GrapesJS are used in CSS Composer inside Rules and in Components as classes. To illustrate this concept let's take
a look at this code:

```css
span > #send-btn.btn{
 ...
}
```

```html
<span>
  <button id="send-btn" class="btn"></button>
</span>
```

In this scenario we get:

*   span     -> selector of type `tag`
*   send-btn -> selector of type `id`
*   btn      -> selector of type `class`

So, for example, being `btn` the same class entity it'll be easier to refactor and track things.

You can customize the initial state of the module from the editor initialization, by passing the following [Configuration Object][1]

```js
const editor = grapesjs.init({
 selectorManager: {
   // options
 }
})
```

Once the editor is instantiated you can use its API and listen to its events. Before using these methods, you should get the module from the instance.

```js
// Listen to events
editor.on('selector:add', (selector) => { ... });

// Use the API
const sm = editor.Selectors;
sm.add(...);
```

## Available Events

*   `selector:add` - Selector added. The [Selector] is passed as an argument to the callback.
*   `selector:remove` - Selector removed. The [Selector] is passed as an argument to the callback.
*   `selector:update` - Selector updated. The [Selector] and the object containing changes are passed as arguments to the callback.
*   `selector:state` - State changed. Passes the new state value as an argument.
*   `selector` - Catch-all event for all the events mentioned above. An object containing all the available data about the triggered event is passed as an argument to the callback.

## Methods

*   [getConfig][2]
*   [add][3]
*   [get][4]
*   [remove][5]
*   [getAll][6]
*   [setState][7]
*   [getState][8]

[Selector]: selector.html

## getConfig

Get configuration object

Returns **[Object][9]** 

## add

Add a new selector to the collection if it does not already exist.
You can pass selectors properties or string identifiers.

### Parameters

*   `props` **([Object][9] | [String][10])** Selector properties or string identifiers, eg. `{ name: 'my-class', label: 'My class' }`, `.my-cls`
*   `opts` **[Object][9]?** Selector options (optional, default `{}`)

### Examples

```javascript
const selector = selectorManager.add({ name: 'my-class', label: 'My class' });
console.log(selector.toString()) // `.my-class`
// Same as
const selector = selectorManager.add('.my-class');
console.log(selector.toString()) // `.my-class`
```

Returns **[Selector]** 

## get

Get the selector by its name/type

### Parameters

*   `name` **[String][10]** Selector name or string identifier
*   `type`  

### Examples

```javascript
const selector = selectorManager.get('.my-class');
// Get Id
const selectorId = selectorManager.get('#my-id');
```

Returns **([Selector] | null)** 

## remove

Remove Selector.

### Parameters

*   `selector` **([String][10] | [Selector])** Selector instance or Selector string identifier
*   `opts`  

### Examples

```javascript
const removed = selectorManager.remove('.myclass');
// or by passing the Selector
selectorManager.remove(selectorManager.get('.myclass'));
```

Returns **[Selector]** Removed Selector

## setState

Change the selector state

### Parameters

*   `value` **[String][10]** State value

### Examples

```javascript
selectorManager.setState('hover');
```

Returns **this** 

## getState

Get the current selector state

Returns **[String][10]** 

## getAll

Get all selectors

Returns **Collection<[Selector]>** 

[1]: https://github.com/artf/grapesjs/blob/master/src/selector_manager/config/config.js

[2]: #getconfig

[3]: #add

[4]: #get

[5]: #remove

[6]: #getall

[7]: #setstate

[8]: #getstate

[9]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[10]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String
