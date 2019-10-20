# Implementation of reCAPTCHA v2 in jsPsych

This script implements the [reCAPTCHA v2](https://developers.google.com/recaptcha/docs/display) function in an online experiment created by [jsPsych](https://github.com/jspsych/jsPsych)  to prevent bots from taking part in it.

## How to use

### Get API key

* Follow [the instruction](https://phppot.com/php/how-to-get-google-recaptcha-site-and-secret-key/) to sign up for an API key pair for your site on [http://www.google.com/recaptcha/admin](http://www.google.com/recaptcha/admin). You need to have a Google account.
* Copy the **Site key** and replace it with `your_site_key` in `recaptcha.html` (an external html file to use reCAPTCHA in jsPsych). Do not copy and paste the Secret key!

```
<div class="g-recaptcha" data-sitekey="your_site_key" data-callback="correctCaptcha">
```

### Call the function in jsPsych

* Locate the core jsPsych and its plugin and css files in appropriate directories.
* Include the following codes in the header section of `index.html` (a main html file to call the jsPsych function) to use the [jspsych-external-html plugin](https://www.jspsych.org/plugins/jspsych-external-html/) and [Google reCAPTCHA API](https://developers.google.com/recaptcha/docs/display).

```
<script src="jspsych-6.0.5/plugins/jspsych-external-html.js"></script>
<script src="https://www.google.com/recaptcha/api.js" async defer></script>
```

* Define the `recaptcha` object in `index.html`, and push it to a jsPsych timeline where you want to activate the reCAPTCHA function in the experiment. Both `recaptcha.html` and `index.html` should be placed in the same directory.

```
// reCAPTCHA object
var recaptcha = {
    type: "external-html",
    url: "recaptcha.html",
    cont_btn: "submit_button",
    execute_script: true
};

var timeline = [];

timeline.push(recaptcha);
```

To test the function locally, using [Visual Studio Code](https://code.visualstudio.com/) with [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extention is easy and helpful.

## Author

Tasuku Igarashi ([@tasukuigarashi](https://github.com/tasukuigarashi))

## Acknowledgments

Ryuichi ([@mjtp0325](https://github.com/mjtp0325))

## License

MIT
