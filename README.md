Guiders.js (version 1.1.2)
=========================

Guiders are a user experience design pattern for introducing users to a web application.  

Live Examples
-----

Here are a couple examples hosted online.  You can also check out `README.html` for guiders in action!

[http://jeffpickhardt.com/guiders/](http://jeffpickhardt.com/guiders/)

[https://optimizely.appspot.com/edit#url=www.google.com](https://optimizely.appspot.com/edit#url=www.google.com)


Setup
-----

Here is sample code for initializing a couple of guiders.  Guiders are hidden when created, unless `.show()` is method chained immediately after `.createGuider`.

~~~ javascript
guiders.createGuider({
  buttons: [{name: "Next"}],
  description: "Guiders are a user interface design pattern for introducing features of software. This dialog box, for example, is the first in a series of guiders that together make up a guide.",
  id: "first",
  next: "second",
  overlay: true,
  title: "Welcome to Guiders.js!"
}).show();
/* .show() means that this guider will get shown immediately after creation. */

guiders.createGuider({
  attachTo: "#clock",
  buttons: [{name: "Close, then click on the clock.", onclick: guiders.hideAll}],
  description: "Custom event handlers can be used to hide and show guiders. This allows you to interactively show the user how to use your software by having them complete steps. To try it, click on the clock.",
  id: "third",
  next: "fourth",
  position: 2,
  title: "You can also advance guiders from custom event handlers.",
  width: 450
});
~~~~

The parameters for creating guiders are:

~~~
attachTo: (optional) selector of the html element you want to attach the guider to
buttons: array of button objects
  {
    name: "Close",
    classString: "primary-button",
    onclick: callback function for when the button is clicked
      (if name is "close" or "next", onclick defaults to guiders.hideAll and guiders.next respectively)
   }
buttonCustomHTML: (optional) custom HTML that gets appended to the buttons div
description: text description that shows up inside the guider
highlight: (optional) selector of the html element you want to highlight (will cause element to be above the overlay)
offset: fine tune the position of the guider, e.g. { left:0, top: -10 }
overlay: (optional) if true, an overlay will pop up between the guider and the rest of the page
position: (optional / required if using attachTo) clock position at which the guider should be attached to the html element
title: title of the guider
width: (optional) custom width of the guider (it defaults to 400px)
xButton: (optional) if true, a X will appear in the top right corner of the guider, as another way to close the guider
classString: (optional) allows for styling different guiders differently based upon their classes
~~~


Integration
-----------

Besides creating guiders, here is sample code you can use in your application to work with guiders:

~~~ javascript
guiders.hideAll(); // hides all guiders
guiders.next(); // hides the last shown guider, if shown, and advances to the next guider
guiders.show(id); // shows the guider, given the id used at creation
~~~

You'll likely want to change the default values, such as the width (set to 400px).  These can be found at the top of `guiders.js` in the `_defaultSettings` object.  You'll also want to modify the css file to match your application's branding.

Lastly, if the URL of the current window is of the form `http://www.myurl.com/mypage.html#guider=foo`, then the guider with id equal to `foo` will be shown automatically.


In Closing
----------

Guiders are a great way to improve the user experience of your web application.  If you're interested in optimizing user experience through A/B testing, check out [Optimizely](http://www.optimizely.com).  We're the people who built Guiders in the first place.

If you have questions about Guiders or Optimizely, email us at `jeff+pickhardt@optimizely.com` or `hello@optimizely.com`.


License
-------

Released under the [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).