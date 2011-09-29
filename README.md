TEASCRIPT
---------

FEATURES
--------
Semicolons are optional
`var` is optional
Argument parens are optional
Local variables can be defined using @, such as `@local_variable`
Implicit 'return'
'function' can also be written as ->
javascript is valid teascript

SYNTAX
------

Example: intake_spec.js

     if (typeof jQuery != 'undefined') {
       spyOn(jQuery.ajaxSettings, 'xhr').andCallFake(
         function() {
           var newXhr = new FakeXMLHttpRequest();
           ajaxRequests.push(newXhr);
           return newXhr;
         });
     }

Becomes: intake_spec.ts
    if defined? jQuery
      spyOn(jQuery.ajaxSettings, 'xhr').andCallFake -> {
          newXhr = new FakeXMLHttpRequest()
          ajaxRequests.push newXhr
      }
    end


Jasmine tests

    it('should unset the "submitting" class on the form', function () {
      var request = mostRecentAjaxRequest();

      expect($form).toHaveClass('submitting');
      request.response(response);
      expect($form).not.toHaveClass('submitting');
    });
Become
    it 'should unset the "submitting" class on the form', -> {
      request = mostRecentAjaxRequest()
      expect($form).toHaveClass 'submitting'
      request.response response
      expect($form).not.toHaveClass 'submitting'
    }


