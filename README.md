# Scooch

A mobile-first content and image carousel.

[![NPM](https://nodei.co/npm/scooch.png?downloads=true)](https://nodei.co/npm/scooch/)
[![Code Climate](https://codeclimate.com/github/mobify/scooch/badges/gpa.svg)](https://codeclimate.com/github/mobify/scooch)
[![Bower version](https://badge.fury.io/bo/scooch.svg)](http://badge.fury.io/bo/scooch)

## Demo

You can find a simple demo on [the Documentation page](http://mobify.github.io/scooch/). More demos can be found inside the `examples` folder in the repo. Run `grunt examples` to see them in Chrome (mobile device emulation is recommended).

## Requirements

* [jQuery](http://jquery.com/)

### Zepto Support

Scooch supports Zepto up until v0.6.1 but is not actively developed for it. You should be able to use Scooch directly with Zepto. While we don't actively support Zepto for Scooch, we welcome any and all issues and PRs to help us make it work.

## Installation

Scooch can be installed using NPM:

```
npm install scooch
```

## Usage

    <!-- include scooch.css -->
    <link rel="stylesheet" href="scooch.css">
    <link rel="stylesheet" href="scooch-style.css">

    <!-- the viewport -->
    <div class="m-scooch m-fluid m-scooch-photos">
      <!-- the slider -->
      <div class="m-scooch-inner">
        <!-- the items -->
        <div class="m-item m-active">
          <img src="image1.jpg">
        </div>
        <div class="m-item">
          <img src="image2.jpg">
        </div>
        <div class="m-item">
          <img src="image3.jpg">
        </div>
      </div>
      <!-- the controls -->
      <div class="m-scooch-controls m-scooch-bulleted">
        <a href="#" data-m-slide="prev">Previous</a>
        <a href="#" data-m-slide="1" class="m-active">1</a>
        <a href="#" data-m-slide="2">2</a>
        <a href="#" data-m-slide="3">3</a>
        <a href="#" data-m-slide="next">Next</a>
      </div>
    </div>

    <!-- include jquery.js -->
    <script src="jquery.js"></script>
    <!-- include scooch.js -->
    <script src="scooch.js"></script>
    <!-- construct the carousel -->
    <script>$('.m-scooch').scooch()</script>


## Classes

By default, items are center aligned and their width is determined by
their content width and/or any styling that restricts their width.

To change the styling of the items, add the following classes to the
viewport:


| Class       | Description                                            |
|-------------|---------------------------------------------------------
| `.m-fluid`  | Causes the width of items to resize to match the viewport width. |
| `.m-center` | Causes the items to be center aligned, not left aligned (the default). |




## Methods

### .scooch(options)

Constructs the carousel with specific options. Defaults are shown here.

    $('.m-scooch').scooch({
          dragRadius: 10,
          moveRadius: 20,
          animate: true,
          autoHideArrows: false,
          rightToLeft: false,
          infinite: false,
          autoplay: false,
          classPrefix: "m-",
          classNames: {
            outer: "scooch",
            inner: "scooch-inner",
            item: "item",
            center: "center",
            touch: "has-touch",
            dragging: "dragging",
            active: "active",
            inactive: "inactive",
            fluid: "fluid"
        }
    });

### Options

The `options` object passed to Scooch during construction can configure its behaviour in the following ways:

| Option          |  Behaviour                                                          |
|-----------------|---------------------------------------------------------------------|
| dragRadius      | The size of the 'deadspace' when dragging before Scooch begins following cursor/finger |
| moveRadius      | The size of the 'deadspace' that must be exceeded before Scooch will move between items |
| animate         | Whether or not Scooch should animate the move between items         |
| autoHideArrows  | Whether or not Scooch should apply the inactive class to its previous and next controls (indicated by `[data-m-slide=prev]` and `[data-m-slide=next]`) when at its "bounds" |
| rightToLeft     | Whether or not Scooch should treat "next" as left and "previous" as right |
| infinite        | Whether or not Scooch should loop on itself                         |
| autoplay: {interval: Number, cancelOnInteraction: Boolean} | Autoplay through the Scooch, advancing items every `interval` milliseconds. `cancelOnInteraction` sets whether or not the autoplay terminates once a user interacts with it. Autoplaying Scooches will always appear to loop as if they are infinite until user interaction, at which point they resume the behaviour specified by their options |
| classPrefix     | What all Scooch's classes will be prefixed by                       |
| classNames      | What Scooch should reference as its class names                     |

### .scooch('next')

Moves the carousel one item to the right (or left if `rightToLeft` option is enabled).

    $('.m-scooch').scooch('next');

### .scooch('prev')

Moves the carousel one item to the left (or right if `rightToLeft` option is enabled).

    $('.m-scooch').scooch('prev');

### .scooch('move', x)

Moves the carousel to a index `x` (1-based).

    $('.m-scooch').scooch('move', 1);

### .scooch('unbind')

Removes event handlers bound on the carousel.

    $('.m-scooch').scooch('unbind');

### .scooch('bind')

Binds the event handlers on the carousel.

    $('.m-scooch').scooch('bind');

### .scooch('refresh')

Re-initialize carousel after new slides were added or removed

    $('.m-scooch').scooch('refresh');

### .scooch('destroy')

Removes the carousel and its event handlers from the DOM.

    $('.m-scooch').scooch('destroy');


## Events

The viewport emits the following events:

| Name          | Arguments                 | Description                               |
|---------------|---------------------------|-------------------------------------------|
| beforeSlide   | previousIndex, newIndex   | Fired before the carousel moves.          |
| afterSlide    | previousIndex, newIndex   | Fired after the carousel begins moving.   |

## Browser Compatibility

### Mobile Browsers

The following mobile browsers are fully supported:

| Browser           | Version |
|-------------------|---------|
| Mobile Safari     | 3.1.3+  |
| Android Browser   | 2.1+    |
| Android Chrome    | 1.0+    |
| Android Firefox   | 1.0+    |

The following mobile browsers have degraded support:

| Browser           | Version |
|-------------------|---------|
| Windows Phone     | 7.5     |

### Desktop Browsers

The follow desktop browsers are fully supported:

| Browser           | Version |
|-------------------|---------|
| Safari            | 4.0+    |
| Firefox           | 4.0+    |
| Chrome            | 12.0+   |
| Opera             | 12.0+   |
| Internet Explorer | 10.0+   |

The following desktop browsers have degraded support:

| Browser           | Version |
|-------------------|---------|
| Internet Explorer | 8.0,9.0 |
| Firefox           | 3.5,3.6 |

## Building a distribution
### Requirements
* [Node.js v4.x LTS + NPM v2.x](https://nodejs.org/en/download/) (Mobify recommends [NVM](https://github.com/creationix/nvm) for installing Node + NPM)
* [Grunt](http://gruntjs.com/)
    * Install with `npm install -g grunt-cli`

### Steps
1. `npm install`
1. `grunt build`

The build directory will be populated with minified versions of the css and
javascript files and a .zip of the original source files (for distribution and
use with whatever build system you might use).

## License

_MIT License. Scooch is Copyright © 2016 Mobify. It is free software and may be redistributed under the terms specified in the LICENSE file._
