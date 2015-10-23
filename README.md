# ll-seance-behavior

Enables an element to perform the following actions on any child (target) elements that also have this behavior, have unique HTML ids, may not yet exist in the local DOM, and may have not reached a desired life-cycle state ('ready', 'attached' or 'detached'):

- Set one or more attribute(s) on the target element.
- Set up a callback function that will be called with the target element as an argument.

Examples of target elements:

- an element inside a dom-if or dom-repeat template
- an element dynamically added to the local DOM

## Usage

1. Add LeisureLinkBehaviors.SeanceBehavior to the parent and child (target) elements.
1. In the parent element, call the seanceBegin method to set some attributes on the target element, like this:
          
        this.seanceBegin('theTableId', 'attached', {items: dataFromServer, title: 'Employees'});
        
        // You can also pass 'ready' or 'detached' as the event.
        // 'created' isn't supported because the behavior doesn't work at that stage.
        
1. In the parent element, call the seanceBegin method to set up a callback, like this:
        
        this.seanceBegin('theTableId', 'attached', null, this.tellMeItAppeared);
        
        // this.tellMeItAppeared will then be called with the target element as the sole argument.
        
1. If you change your mind:

        this.seanceEnd('theTableId', 'attached');

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install
