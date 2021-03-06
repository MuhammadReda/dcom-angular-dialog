#dcom-angular-dialog
[doodeec.com](http://doodeec.com)

##Version
0.9.2

##Description
This is a dialog module for angular, which uses Bootstrap 3 modals style.
It creates `dialogService` in your app.

dialogService allows you to create dialog in this way:

    dialogService.create(templateName, options);

for example

    var dialog = dialogService.create('error', {
        className: 'errorDialog',
        controller: { message: "scope message" },
        persistent: true,
        backdrop: false
    });

and call different methods:

    dialog.open()
    dialog.close()
    dialog.dismiss()
    dialog.destroy()

or register a custom callStack on these events:

- open
- ready (called once template for modal is resolved - resolving template starts directly inside modal constructor)
- dismiss
- destroy (when modal is being destroyed, it gets dismissed first, so dismissed stack is called also)

like this

    dialog.on('open', function() {/* callback */})
    

Closing the modal with ESC key, or with Backdrop click event are both supported. Closing with Backdrop click can be
disabled by setting `backdrop` option to false when creating a modal.

###Usage
Include `dcom-angular-dialog-{version}.min.js` and `dcom-angular-dialog-{version}.min.css`,
and in the app module definition add `dcModal` as required module

    angular.module('myApp', ['dcModal'])...

###Parameters
    
    - templateName
        name of html template defined for the modal, will be searched in templates folder by default (relative path)
    - options
        object of additional options

###Supported Modal Options

    - className     {string}
        CSS class of the root dialog element
    - controller    {Function/Object}
        controller function or object with scope definition to be used inside modal
    - persistent    {Boolean}
        defines if .close() method hides modal or removes it completely from DOM
    - backdrop      {Boolean}
        when false, it disables closing of the dialog on backdrop click
    - animate       {Boolean}
        when false, modal is not animated when displaying (true by default)

###Overwrite default template folder for your application
You can set where your templates are located by setting the value of `TEMPLATE_FOLDER`
after your module's initialization. (If no value is set, the value defaults to `/`)

    angular.module('dcModal')
        .value('TEMPLATE_FOLDER', 'path/to/templates/folder');

This means when you call `dialogService.create('error');`,
this will load the template **/path/to/templates/folder/error.html**.

### Set application's default template
Set application's default template by setting the value of `DEFAULT_TEMPLATE_FILE`
after your module's initialization. (If no value is set, the value defaults to `templates/default.html`)

    angular.module('dcModal')
        .value('DEFAULT_TEMPLATE_FILE', 'path/to/default/template.html');

###Credits
Thanks to [capaj](http://github.com/capaj) for the initial idea.


###Licence
Released under MIT licence.

###Support
Tested across Angular 1.0.6, 1.2.14 and 1.3.8.

If you encounter any problems using this module, contact me via [doodeec.com](http://doodeec.com)
or [send me an email](mailto:doodeec@gmail.com)

###Contribution
If you want to make this code better, feel free to open a PR
