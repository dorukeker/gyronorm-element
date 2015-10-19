# gyronorm-element
Element wrapper for [gyronorm.js](https://github.com/dorukeker/gyronorm.js), a JavaScrip library that accesses the gyroscope and accelerometer data from the web browser and combines them in one JS object.

This element wraps the gyronorom.js library in an HTML element using Polymer. It exposes the public API of gyronorm.js as attributes and functions.

Below are the details of the HTML element and basic usage. If you want information on the JavaScript version of gyronorm.js, please visit the [GitHub page](https://github.com/dorukeker/gyronorm.js).

## Installation
Use Bower or NPM

```sh
$ bower install gyronorm-element
```

or

```sh
$ npm install gyronorm-element
```

## How to add
Use the HTML imports to add it to your HTML file.

```html
...

<link rel="import" href="[path to the element]/gyronorm-element.html">

...
```

## How to use
Use the element like any other HTML elements in the `<body></body>` section.

```html
...

<body>

	<gyronorm-element></gyronorm-element>

</body>

...
```

When the element is rendered, the gyronorm object is initilized with default values, and start to provide deviceorientation and devicemotion data. So the element is ready to use.

You can use attributes to access this data and/or change the default options.

The attributes and functions are explained below.

### Attributes

#### Gyroscope and accelerometer values
Gyronorm.js provides the values of gyroscope and accelerometer in one object. The wrapper element has attributes to provide these values as separate attributes.

After the element is rendered, the following attributes will update and provide values (every millisecond defined in the frequency attribute.)

You can bind a variable to those attribute on host element. So this variable will reflect the updated values. Below is an example.

```html
<body>

	<gyronorm-element alpha="{{alphaValue}}"></gyronorm-element>

	<paper-input label="alpha" value="[[alphaValue]]" disabled></paper-input>

</body>

```

Here is a list of these attributes

- alpha
- beta
- gamma
- acceleration-x
- acceleration-y
- acceleration-z
- gravity-x
- gravity-y
- gravity-z
- rotation-rate-alpha
- rotation-rate-beta
- rotation-rate-gamma

Please note that these values are all read-only and can be used only to pass the data from gyronorm-element to the host element.

#### Log messages
Gyronorm.js library sends log and error messages. The element exposes these messages in an attribute called `log-message`. You can bind to this attribute and display the messages. Below is an example.

```html
<body>

	<gyronorm-element log-message="{{message}}"></gyronorm-element>

	<paper-input label="Log Message" value="[[message]]" disabled></paper-input>

</body>

```

#### Options
The element exposes the initial options of Gyronorm.js as attributes. If you want to learn more about the options and what they do you can check the [gyronorm.js README.md](https://github.com/dorukeker/gyronorm.js)

Note that when you change the values of these attributes, the GyroNorm object is stopsed and reinitiated under the hood. Chaging them very frequently might be costly on performance.

Here is a list of attributes and expected values

- decimal-count (Integer)
- frequency (Integer)
- gravity-normalized (Boolean)
- orientation-base (String - `world` or `game`)
- screen-adjusted (Boolean)

The demo file shows details how you can use those attributes.

### Function
The element exposes only one function from the gyronorm object. The rest can be handled with attributes.

#### setHeadDirection
You can call this only when `screen-adjusted` is set to `false`. After it is called, the element will start to return `alpha` values relative to the current head direction of the device.

```html
<body>

	<gyronorm-element id="gyronorm" alpha="{{alpha}}"></gyronorm-element>

	<paper-input label="alpha" value="[[alpha]]" disabled></paper-input>

	<!-- When youclick this button, the gyronorm-element wil update the head direction -->
	<paper-button class="colorful" onclick="_setHeadDirection()">Set head direction</paper-button>

	<script>

		var _setHeadDirection = function(){

			var gnElement = document.getElementById('gyronorm');
			gnElement.setHeadDirection();

		}

	</script>


</body>
```
