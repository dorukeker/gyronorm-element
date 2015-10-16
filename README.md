# gyronorm-element
Element wrapper for [gyronorm.js](https://github.com/dorukeker/gyronorm.js), a JavaScrip library that accesses the gyroscope and accelerometer data from the web browser and combines them in one JS object.

This element wraps the gyronorom.js library in an HTML element using Polymer. It exposes the public API of gyronorm.js as attributes and functions.

Below are the details of the HTML element and basic usage. If you want information on the JavaScript version of gyronorm.js, please visit the [GitHub page](https://github.com/dorukeker/gyronorm.js).

## Installation

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

When the element is rendered, the gyronorm object is initilized with default values, and start to provide deviceorientation and devicemotion data.

You can use attributes to access this data and/or change the default options.

The attributes and functions are explained below.

### Attributes

#### Gyroscope and accelerometer values
Gyronorm.js provides the values of gyroscope and accelerometer in one object. The wrapper element has attributes to provide these values as separate attributes.

After the element is rendered the following attributes will update and provide values (every millisecond defined in the frequency attribute.)

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

Please note that these values are all read-only and can be used only to pass the data from child element to the host element.

#### Log messages


#### Options


### Function
