# Dessert Showdown

Clone of [showdown](https://github.com/showdownjs/showdown) implemented in Rust for WebAssembly

## Summary
* [Installation](#installation)
* [Quick Example](#quickexample)

## Installation
```sh
npm install dessert-showdown
```

## Quick Example

### Node

```js
var showdown  = require('dessert-showdown'),
    converter = new showdown.Converter(),
    text      = '# hello, markdown!',
    html      = converter.makeHtml(text);
```

### Output 

This example should output...

```html
    <h1 id="hellomarkdown">hello, markdown!</h1>
```

## Options

You can change some of dessert-showdown's default behavior through options. 

### Setting options

Options can be set:

#### Globally

Setting a "global" option affects all instances of dessert-showdown

```js
showdown.setOption('optionKey', 'value');
```

#### Locally
Setting a "local" option only affects the specified Converter object. 
Local options can be set:

 * **through the constructor**
    ```js
    var converter = new showdown.Converter({optionKey: 'value'});
    ```

 * **through the setOption() method**
    ```js
    var converter = new showdown.Converter();
    converter.setOption('optionKey', 'value');
    ```

### Getting an option

Dessert-showdown provides 2 methods (both local and global) to retrieve previous set options.

#### getOption()

```js
// Global
var myOption = showdown.getOption('optionKey');

//Local
var myOption = converter.getOption('optionKey');
```

#### getOptions()

```js
// Global
var showdownGlobalOptions = showdown.getOptions();

//Local
var thisConverterSpecificOptions = converter.getOptions();
```

### Valid Options

 * **noHeaderId**: (boolean) [default false] Disable the automatic generation of header ids.
 
 * **headerLevelStart**: (integer) [default 1] Set the header starting level. For instance, setting this to 3 means that

    ```md
    # foo
    ```
    will be parsed as 
    
    ```html
    <h3>foo</h3>
    ```

 * **literalMidWordAsterisks**: (boolean) [default false] Turning this on will stop dessert-showdown from interpreting asterisks
   in the middle of words as `<em>` and `<strong>` and instead treat them as literal asterisks.
   
 * **strikethrough**: (boolean) [default false] Enable support for strikethrough syntax.
   `~~strikethrough~~` as `<del>strikethrough</del>`
   
 * **tables**: (boolean) [default false] Enable support for tables syntax. Example:
    
   ```md
   | h1    |    h2   |      h3 |
   |:------|:-------:|--------:|
   | 100   | [a][1]  | ![b][2] |
   | *foo* | **bar** | ~~baz~~ |
   ```

 * **tasklists**: (boolean) [default false] Enable support for GFM tasklists. Example:
 
   ```md
    - [x] This task is done
    - [ ] This is still pending
   ```

 * **simpleLineBreaks**: (boolean) [default false] Parses line breaks as `<br>`, without
   needing 2 spaces at the end of the line
 
   ```md
   a line  
   wrapped in two
   ```
    
   turns into:
    
   ```html
   <p>a line<br>
   wrapped in two</p>
   ```

## Credits
Showdown full credit list at https://github.com/showdownjs/showdown/blob/master/CREDITS.md

