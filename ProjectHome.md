# Introduction #

Take advantage of HTML5 placeholders today with IE and older browsers. Furthermore, as an enhancement, assign a custom class (default is "placeholder") to placeholder text which will automatically swap out when user focuses on the the field.

# Brief Summary #

Features:
  * Complete placeholder emulation in Internet Explorer and older browsers including password placeholders.
  * Class assignment to placeholder text for custom styling.
  * Auto-loads for convenience. (Can be disabled)
  * Configurable and provides additional workarounds if needed.
  * Designed to work fast--detects browser capabilities and does not execute code where not necessary.

# Use & Configurations #

Simply include the plugin after loading jQuery (tested with 1.4.4+). The minimum requirement for this plugin to work is just this

```

<script type="text/javascript" src="/javascripts/jquery.complete-placeholder.min.js">

Unknown end tag for &lt;/script&gt;


```

You can also configure the plug-in. Here is an example an example that utilizes all possible variables.
```

<script type="text/javascript">

$(document).placeholder({
'set_class'  	   : true,
'class_name' 	   : 'placeholder',
'skip'  		   : false,
'ie_submit_swap' 	   : true, // If fallback validation isn't working in IE try setting to false.
'ie_password_callback' : '' // Takes string to analyze and returns boolean. Workaround for if swap doesn't work.
})



Unknown end tag for &lt;/script&gt;



```

If the script is not configured it will automatically load with default settings, shown above, unless the 'skip' parameter is set to true and passed to the script (in which case it will not load at all). Here is a brief description of these parameters.

| **Parameter** | **Description** |
|:--------------|:----------------|
| set\_class    | Default is true. This tells the plugin to assign a special class to placeholder text.|
| class\_name   | This is the name of the class set to the placeholder text.|
| skip          | If the plugin is included, it will automatically load. If for some reason it is included but the we don't want it to automatically load, we set this parameter to true.|
| ie\_submit\_swap | Special tricks have to be used for IE. We have to swap the fields back and forth so that we can show placeholder text then turn it back into a password field. This emulates HTML5 browser behavior for placeholders on password field in IE. A problem that can arise when the form is submitted due to the nature of field swapping in IE. Validation that load after (or before) the registers one field but a different one (due to the swap) may be submitted. In this case, event assignments on the original field will not work. Therefore, with this option set to true, we turn the field into text just after submit then back to password on validation failure. With this option false the password field is submitted and no other swapping occurs during the submit phase. |
| ie\_password\_callback | In case the above method does not work. We can explicitly invoke a callback function. The plugin will pass the value of the password field to this function and expect back a boolean. True mean that the field passed validation. False mean that if failed.|