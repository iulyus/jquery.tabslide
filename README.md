Tabslide
===============

With Tabslide you can create tabbed content or sliders easily with a simple fading effect, nothing fancy.

**Requires:** jQuery 1.9+, [Advanced jQuery Boilerplate](https://github.com/elclanrs/advanced-jquery-boilerplate)

## How to

A tabslide has 3 main modules:

#### 1. Container

A main container to wrap your tabslider.

```html
<div class="tabslide-container">
  <!-- Tabslide -->
</div>
```
Once you have the container call the plugin.

```javascript
var $tabslider = $('.tabslide-container').tabslide({ options });
```

#### 2. Navigation

By default Tabslide will generate a numbered pagination, but you can pass custom text for each slide, or even make your own markup:

To use the default pagination you only need to create a container and Tabslide will generate the numbers for you.
```html
<nav class="tabslide-nav"></nav>
```

To use custom text, create the container and pass an array with the text of each slide in order.
```html
<nav class="tabslide-nav"></nav>
```
```javascript
$('.tabslide-container').tabslide({
  buildNavItems: [
    'First Slide',
    'Second Slide',
    'Third Slide'
  ]
});
```

#### 3. Slides

The slides must be inside a wrapper. A slide can be an image or an article with content or any other custom markup.

```html
<div class="tabslide-wrap">

  <article class="slide">
    <!-- content -->
  </article>

  <article class="slide">
    <!-- content -->
  </article>

  <article class="slide">
    <!-- content -->
  </article>

</div>
```

#### 4. Next/Previous (optional)

The next and previous buttons are up to you. Tabslide provides two shortcut methods.

```javascript
$('.prev').click(function(){ $tabslider.tabslide('prev') });
$('.next').click(function(){ $tabslider.tabslide('next') });
```

## Options

```javascript
defaults = {
  nav: '.tabslide-nav', // navigation container
  navItems: 'li', // navigation item selector
  // `true` for default pagination
  // `false` for your own custom markup
  // Pass an array with custom text for each slide
  buildNavItems: true,
  wrap: '.tabslide-wrap', // the container for the slides
  item: '.slide', // selector for a single slide
  activeClass: 'slide-active', // the class for active item in navigation
  before: null, // callback that runs before changing slides
  after: null, // callback that runs after changing slides
  fadeSpeed: 300 // the speed of the fading effect. 0 to disable
};
```

## Methods

#### go(idx)

Go to a specific slide by index.

```javascript
$tabslider.tabslide('go', 2); // go to slide in index 2
```

#### prev/next

Go to the previous or next slide.

```javascript
$tabslider.tabslide('prev'); // go to previous slide
$tabslider.tabslide('next'); // go to next slide
```

## FAQ

**How can I hide the previous and next buttons on the first and last slide respectively?**  

```javascript
$('.tabslide-container').tabslide({
  // Add some logic after the slides change
  // `this` is the Tabslide instance
  // `idx` is the index of the active slide
  after: function(idx) {
    // Reset
    $('.prev, .next').show();
    // If it's the first slide hide the previous button
    if (idx === 0) $('.prev').hide();
    // If it's the last slide hide the next button
    if (idx >= this.$items.length-1) $('.next').hide();
  }
});

$('.prev').hide(); // init, assuming you start on the first slide
```
