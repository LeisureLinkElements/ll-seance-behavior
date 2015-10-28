# Séance Behavior

Enables an element to perform the following actions on any child (target) elements
that also have this behavior, have unique HTML ids, may not yet exist in the local DOM,
and may have not reached a desired life-cycle state ('ready', 'attached' or 'detached'):

- Set one or more attribute(s) on the target element.
- Set up a callback function that will be called with the target element as an argument.

NOTE: In both cases (setting attributes or setting a callback), the seance actions are only performed once,
even if the target element detaches and reattaches later.

Examples of target elements:

- an element inside a dom-if or dom-repeat template
- an element dynamically added to the local DOM

Usage:

1. Add LeisureLinkBehaviors.SeanceBehavior to the parent and child (target) elements.

          behaviors: [LeisureLinkBehaviors.SeanceBehavior],

1. The parent element can then call the seanceBegin method to set some attributes on the target element, like this:

          this.seanceBegin('theTableId', 'attached', {
            items: dataFromServer,
            title: 'Employees'
          });

1. The parent element can also call the seanceBegin method to set up a callback, like this.
When the target element is attached (if not already),
this.tellMeAboutIt is called with the target element as the only argument.

          this.seanceBegin('theTableId', 'attached', null, this.tellMeAboutIt);

1. If the target element hasn't attached yet, this will prevent those actions from being performed:

          this.seanceEnd('theTableId', 'attached');

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install
