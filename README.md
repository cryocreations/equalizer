# equalizer.js

A lightweight jQuery plugin to equalize element heights.

## Features

* Equalize the heights of any element
* Responsive control with breakpoint handling
* Handles `padding`, `border` properties
* Use HTML data attributes to initialize and customize Equalizer without using javascript
* Callback events
* Minimum and maximum height limiting
* Toggle class names for inactive and active equalized elements
* Increased performance
* Tested in IE, Chrome, Firefox, Safari
* Only 2kb

## Requirements

This plugin requires jQuery 1.7+

## Getting Started

* [Offical documentation](https://www.mattfrazee.com/code/js/equalizer/)

## Installing

Add the script after the jQuery library. Adding this code before the end of the `<body>` tag is preferred.

```html
<script src="equalizer.min.js"></script>
```

## Basic Usage

There are two ways that Equalizer can be used: the HTML data attribute or using jQuery. In HTML, only child elements within the target will be equalized and will not exceed the scope. It is recommended to use the HTML attribute unless you need event callbacks.

### Using HTML data attributes

```html
<div class="row" data-eq>
  <div class="column" data-eq-band><br>
    <p>Bacon ipsum dolor amet ham alcatra jowl beef pastrami chuck kevin capicola. Bacon ribeye pork belly pancetta short loin flank.</p>
  </div>
  <div class="column" data-eq-band><br>
    <p>Swine capicola porchetta, salami tri-tip pork loin pork t-bone hamburger jowl chuck landjaeger ribeye flank. Prosciutto boudin cupim, shankle tail rump salami shoulder.</p>
  </div>
  <div class="column" data-eq-band><br>
    <p>Ribeye ham alcatra jowl kielbasa chicken doner short loin biltong tenderloin.</p>
  </div>
  <div class="column" data-eq-band><br>
    <p>Short loin kielbasa rump, pork belly boudin kevin drumstick jerky meatloaf frankfurter leberkas pancetta corned beef hamburger burgdoggen. Cow pancetta beef, corned beef prosciutto chicken tail shoulder filet mignon.</p>
  </div>
</div>
```

### Using jQuery

```html
<div class="row" id="example">
  <div class="column"><br>
    <p>Bacon ipsum dolor amet ham alcatra jowl beef pastrami chuck kevin capicola. Bacon ribeye pork belly pancetta short loin flank.</p>
  </div>
  <div class="column"><br>
    <p>Swine capicola porchetta, salami tri-tip pork loin pork t-bone hamburger jowl chuck landjaeger ribeye flank. Prosciutto boudin cupim, shankle tail rump salami shoulder.</p>
  </div>
  <div class="column"><br>
    <p>Ribeye ham alcatra jowl kielbasa chicken doner short loin biltong tenderloin.</p>
  </div>
  <div class="column"><br>
    <p>Short loin kielbasa rump, pork belly boudin kevin drumstick jerky meatloaf frankfurter leberkas pancetta corned beef hamburger burgdoggen. Cow pancetta beef, corned beef prosciutto chicken tail shoulder filet mignon.</p>
  </div>
</div>
```

```js
$(document).ready(function(){
	$('#example .column').equalizer();
});
```

## Options

Below are the available settings and the default value that gets passed to the `equalizer()` function. You can also modify defaults directly in the **equalizer.js** file.

Setting | Type | Default | Description
--- | --- | --- | ---
**unequalize** | `Number` | `0` | When the window viewport is lower than this value (in pixels), Equalizer will disable equalizing methods and revert the targets to their natural height.
**minimum** | `Number` | `null` | Sets the minimum height to each target.
**maximum** | `Number` | `null` | Stop the target's height from exceeding this value.
**overflowScroll** | `Boolean` | `false` | This value will enable/disable scrolling of the target if the inner content is larger then element height. *Note: this setting only works in conjuction with the "maximum" option.*
**unequalizedClass** | `String` | `unequalized` | This CSS class will be added to each target that is not equalized. *Note: this setting only works in conjuction with the "unequalize" option.*
**equalizedClass** | `String` | `equalized` | This CSS class will be added to each target that is equalized.

## Options Examples

### Using HTML data attributes

```html
<div class="row" data-eq=".column" data-eq-settings='{"unequalize":0, "minimum":null, "maximum":null, "overflowScroll":false, "equalizedClass":"equalized", "unequalizedClass":"unequalized"}'>
  <div class="column"><br>
    <p>Bacon ipsum dolor amet ham alcatra jowl beef pastrami chuck kevin capicola. Bacon ribeye pork belly pancetta short loin flank.</p>
  </div>
  <div class="column"><br>
    <p>Swine capicola porchetta, salami tri-tip pork loin pork t-bone hamburger jowl chuck landjaeger ribeye flank. Prosciutto boudin cupim, shankle tail rump salami shoulder.</p>
  </div>
  <div class="column"><br>
    <p>Ribeye ham alcatra jowl kielbasa chicken doner short loin biltong tenderloin.</p>
  </div>
  <div class="column"><br>
    <p>Short loin kielbasa rump, pork belly boudin kevin drumstick jerky meatloaf frankfurter leberkas pancetta corned beef hamburger burgdoggen. Cow pancetta beef, corned beef prosciutto chicken tail shoulder filet mignon.</p>
  </div>
</div>
```
#### Note: you cannot use callbacks in the HTML data attributes.

### Using jQuery

```html
<div class="row" id="example">
  <div class="column"><br>
    <p>Bacon ipsum dolor amet ham alcatra jowl beef pastrami chuck kevin capicola. Bacon ribeye pork belly pancetta short loin flank.</p>
  </div>
  <div class="column"><br>
    <p>Swine capicola porchetta, salami tri-tip pork loin pork t-bone hamburger jowl chuck landjaeger ribeye flank. Prosciutto boudin cupim, shankle tail rump salami shoulder.</p>
  </div>
  <div class="column"><br>
    <p>Ribeye ham alcatra jowl kielbasa chicken doner short loin biltong tenderloin.</p>
  </div>
  <div class="column"><br>
    <p>Short loin kielbasa rump, pork belly boudin kevin drumstick jerky meatloaf frankfurter leberkas pancetta corned beef hamburger burgdoggen. Cow pancetta beef, corned beef prosciutto chicken tail shoulder filet mignon.</p>
  </div>
</div>
```

```js
$(document).ready(function(){
	$('#example .column').equalizer({
		unequalize:0,
		minimum:null,
		maximum:null,
		overflowScroll:false,
		equalizedClass:'equalized',
		unequalizedClass:'unequalized'
	});
});

```

## Callbacks

Below are the available settings and their default values that get passed to the `equalizer()` function. You can also modify defaults directly in the **equalizer.js** file.

Setting | Type | Default | Returns | Description
--- | --- | --- | --- | ---
**onEqualize** | `Function` | `null` | `Object` | This function will fire every time the targets have increased or decreased height. This occurs when the viewport width or device orientation changes.
**onUnequalize** | `Function` | `null` | `Object` | This function will fire when the the unequilize value has been met. *Note: this is dependent on the "unequalize" setting.*


## Callback Examples

```html
<div class="row" id="example">
  <div class="column"><br>
    <p>Bacon ipsum dolor amet ham alcatra jowl beef pastrami chuck kevin capicola. Bacon ribeye pork belly pancetta short loin flank.</p>
  </div>
  <div class="column"><br>
    <p>Swine capicola porchetta, salami tri-tip pork loin pork t-bone hamburger jowl chuck landjaeger ribeye flank. Prosciutto boudin cupim, shankle tail rump salami shoulder.</p>
  </div>
  <div class="column"><br>
    <p>Ribeye ham alcatra jowl kielbasa chicken doner short loin biltong tenderloin.</p>
  </div>
  <div class="column"><br>
    <p>Short loin kielbasa rump, pork belly boudin kevin drumstick jerky meatloaf frankfurter leberkas pancetta corned beef hamburger burgdoggen. Cow pancetta beef, corned beef prosciutto chicken tail shoulder filet mignon.</p>
  </div>
</div>
```

```js
$(document).ready(function(){
	$('#example .column').equalizer({
		onEqualize:function(){
			console.log('Equalized!');
		},
		onUnequalize:function(){
			console.log('Unequalized!');
		}
	});
});
```

## Change Log

* Version 1.0
   * Launched plugin

For the versions available, see the [tags on this repository](https://github.com/cryocreations/equalizer/tags).

## Author

**[Matt Frazee](https://www.mattfrazee.com/)** | [GitHub](https://www.github.com/cryocreations) | [Twitter](https://www.twitter.com/cryocreations) | [Stack Overflow](http://stackoverflow.com/users/1650605/matt-frazee)

See also the list of [contributors](https://github.com/cryocreations/equalizer/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
