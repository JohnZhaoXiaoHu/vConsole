Public Properties & Methods
==============================

Some useful vConsole properties and methods are available for plugin development.

## Properties


### vConsole.version

The current version of vConsole.

- Readonly
- Type: string

Example:

```javascript
vConsole.version // => "3.4.1"
```


### vConsole.option

A configuration object.

- Writable
- Type: object

Key                   | Type     | Optional | Default value                               | Description
--------------------- | -------- | -------- | ------------------------------------------- | -------------------
defaultPlugins        | Array    | true     | ['system', 'network', 'element', 'storage'] | Listed built-in plugins will be inited and loaded into vConsole. 
onReady               | Function | true     |                                             | Trigger after vConsole is inited and default plugins is loaded.
onClearLog            | Function | true     |                                             | Trigger after click "Clear" button in Log and System panel.
maxLogNumber          | Number   | true     | 1000                                        | Overflow logs will be removed from log panels.
disableLogScrolling   | Boolean  | true     |                                             | If `false`, panel will not scroll to bottom while printing new logs.
theme                 | String   | true     | 'light'                                     | Theme mode, 'light' | 'dark'.

Example:

```javascript
// get
vConsole.option // => {...}
// set
vConsole.setOption('maxLogNumber', 5000);
// or:
vConsole.setOption({maxLogNumber: 5000});
```


## Methods


### vConsole.setOption(keyOrObj[, value])

Update `vConsole.option`.

##### Parameters:
- (required) keyOrObj: The key of option, or a key-value object.
- (optional) value: The value of an option.

##### Return:
- None

##### Example:

```javascript
vConsole.setOption('maxLogNumber', 5000);
// or:
vConsole.setOption({maxLogNumber: 5000});
```


### vConsole.setSwitchPosition(x, y)

Update the position of switch button.

##### Parameters:
- (required) x: X coordinate, the origin of the coordinate is at the bottom right corner of the screen.
- (required) y: Y coordinate, the origin of the coordinate is at the bottom right corner of the screen.

##### Return:
- None

##### Example:

```javascript
vConsole.setSwitchPosition(20, 20);
```


### vConsole.destroy()

Destroy an vConsole instance object and remove vConsole panel from document.

##### Parameters:
- None

##### Return:
- None

##### Example:

```javascript
var vConsole = new VConsole();
// ... do something
vConsole.destroy();
```


### vConsole.addPlugin(plugin)

Add a new plugin to vConsole. Duplicate plugin will be ignored.

##### Parameters:
- (required) plugin: An VConsolePlugin object.

##### Return:
- Boolean: `true` for success, `false` for failure.

##### Example:

```javascript
var myPlugin = new VConsolePlugin('my_plugin', 'My Plugin');
vConsole.addPlugin(myPlugin);
```


### vConsole.removePlugin(pluginID)

Remove an existing plugin.

##### Parameters:
- (required) pluginID: A string, plugin's id.

##### Return:
- Boolean: `true` for success, `false` for failure.

##### Example:

```javascript
vConsole.removePlugin('my_plugin');
```


### vConsole.showPlugin(pluginID)

Activating a panel according to its plugin id.

Plugin event `hide` will be triggered for previous actived panel, and `show` for current actived panel.

##### Parameters:
- (required) pluginID: A string, panel's plugin id.

##### Return:
- None

##### Example:

```javascript
vConsole.showPlugin("system"); // show System panel
```


### vConsole.show()

Show vConsole panel. This method will trigger plugin event `showConsole`.

##### Parameters:
- None

##### Return:
- None

##### Example:

```javascript
vConsole.show();
```


### vConsole.hide()

Hide vConsole panel. This method will trigger plugin event `hideConsole`.

##### Parameters:
- None

##### Return:
- None

##### Example:

```javascript
vConsole.hide();
```


### vConsole.showSwitch()

Show vConsole switch button.

##### Parameters:
- None

##### Return:
- None

##### Example:

```javascript
vConsole.showSwitch();
```


### vConsole.hideSwitch()

Hide vConsole switch button. 

After the button is hidden, the user will not be able to call vConsole manually. The button or panel must be shown programmably via `vConsole.showSwitch()` or `vConsole.show()`.

##### Parameters:
- None

##### Return:
- None

##### Example:

```javascript
vConsole.hideSwitch();
```


[Back to Index](./a_doc_index.md)