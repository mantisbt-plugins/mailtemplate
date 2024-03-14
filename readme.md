
# Enabling HTML emails within Mantisbt

This is not a plugin but a guide to use templated HTML emails within MantisBT.<br>
Since this does require adjusting one(1) core file, i have prepared that file for two(2) versions:<br>
- 2.25
- 2.26
<br>
Version 20240314

## Copyright

	- 2020/2024 Cas Nuy (www.NUY.info)
	
## License                                                                                    

Released under the [GPL v3 license](http://opensource.org/licenses/GPL-3.0).

## Requirements
	- MantisBT version 2.0.0

## Installation

Please make a backup of the following files from your mantis installation:
config/config_inc.php	( entries need to be added )
core/email_api.php	( here i made changes to core, marked with "## CN" )
In case you are running 2.25 or 2.26, copy the correspong email_api.php into the core directory of your Mantisbt installation.<br>
Ensure you rename it again to "email_api.php"<br>

In case you are running a different version from 2.25 or 2.26:<br>
Copy  template_api.php from the core directory of the distribution to the core directory of your mantis installation.<br>
Make a backup copy of email_api.php in the core directory of your mantis installation.<br>
Next make same changes as found in my version of email_api.php (changes have been marked with "## CN").<br>

Nothing will change yet, everything works as before.<br>
Next open up entries-config_inc.php and add these to your mail settings in your config_inc.php. <br>
As of now the adjusted scripts will kick in.<br>

In case you want to de-activate the functionality, just change:<br>
$g_use_mailtemplate = ON;<br>
into<br>
$g_use_mailtemplate = OFF;<br>

## Configuration

Basic configuration is done within config/config_inc.php, lay-out of the emails you need to adjust/maintain.<br>

### config/config_inc.php

- $g_use_mailtemplate		= ON;
- $g_escape_mailtemplate	= OFF;

Next we need to define the names & locations for the templates, do ensure the web-user has access to the directory.<br>
There are 3 different templates available, make sure that youprovide correct information.<br>
- $g_newbug_mailtemplate	= "/var/www/html/mantis2/core/templates/newbug_mailtemplate.html";
- $g_bug_mailtemplate		= "/var/www/html/mantis2/core/templates/bug_mailtemplate.html";
- $g_note_mailtemplate		= "/var/www/html/mantis2/core/templates/note_mailtemplate.html";

### Template lay-outs

You can make your own lay-out. In the current examples an overview is available which data elements can be used.<br>
Even logo's are supported just like on an other HTML page.

## Support

File bug reports and submit questions on the
[GitHub issues tracker](http://github.com/mantisbt-plugins/mailtemplate/issues).

## Warning

Remember that when upgrading you will need to adjust core/email_api.php again:(

## Remarks
Please let me know how to further improve.....<br>
 
Have a blast!

## changes

08-10-2020	Initial version<br>
26-10-2020	Bugfixes<br>
25-06-2022	Added Escape funtion<br>
			Added special template for new issues<br>
17-08-2022	Made the Escape function configurable (config_inc.php & core/email_api.php)<br>
			Fixed minor lay-out issues in template_api.php<br>
14-03-2024	Added improved readme<br>
			Added sample email_api.php for MantisBT version 2.26<br>
