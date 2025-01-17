
# Enabling HTML emails within Mantisbt

This is not a plugin but a guide to use templated HTML emails within MantisBT.

Version 20250104

## Copyright

	- 2020/2025 Cas Nuy (www.NUY.info)
	
## License                                                                                    

Released under the [GPL v3 license](http://opensource.org/licenses/GPL-3.0).

## Requirements
	- MantisBT version 2.25 or higher

## Installation

1. Backup the following files from your Mantis installation:
    - `config/config_inc.php` 
    - `core/email_api.php` 

2. Next, perform the following copy operations:
    a. Copy `~/distribution/core/template_api.php` into `~/mantis/core/` folder.
    b. Copy `~/distribution/core/templates/` folder into `~/mantis/core/` folder.

3. If using Mantis 2.25:
    - Copy `~/distribution/core/email_api-225.php` to `~/mantis/core/` folder.

4. If using Mantis 2.26:
    - Copy `~/distribution/core/email_api-226.php` to `~/mantis/core/` folder.

5. If using Mantis 2.27:
    - Copy `~/distribution/core/email_api-227.php` to `~/mantis/core/` folder.

5. For Mantis 2.25, 2.26 and 2.27:
    - Rename `~/mantis/core/email_api-XXX.php` to `~/mantis/core/email_api.php`.

7. Next, edit `~/distribution/config/entries-config_inc.php`:
    - Change paths below to reflect the actual path to your Mantis installation (typically `/var/www/html/`, but may vary):
        - `$g_newbug_mailtemplate = "/path/to/mantis/core/templates/newbug_mailtemplate.html";`
        - `$g_bug_mailtemplate = "/path/to/mantis/core/templates/bug_mailtemplate.html";`
        - `$g_note_mailtemplate = "/path/to/mantis/core/templates/note_mailtemplate.html";`

8. Finally, paste entire text in `~/distribution/config/entries-config_inc.php` to the bottom of `~/mantis/config/config_inc.php`.


## Configuration

Basic configuration is done within config/config_inc.php:

### config/config_inc.php

- $g_use_mailtemplate		= ON;  # OFF will disable mailhtml
- $g_escape_mailtemplate	= OFF;
- $g_default_email_bugnote_limit= 0;   # Standard mantis setting (Users can override this in their account settings.)

### Template lay-outs

After installation, template files are located in ~/mantis/core/templates/

Three layouts are provided:
- bug_mailtemplate.html
- newbug_mailtemplate.html
- note_mailtemplate.html

Various fields from Mantis may be inserted into the templates. A full list of available Mantis fields are located at the top of each template file. 

Each file is fully customizable. Logos are also supported via img tags. 

Back up files prior to making edits. 

## Support

File bug reports and submit questions on the
[GitHub issues tracker](http://github.com/mantisbt-plugins/mailtemplate/issues).

## Warning

Remember that when upgrading you will need to adjust core/email_api.php again:(<br>
In case there is no prepared email-api.php, you can do it manual.<br>
All entries are marked with a start and ending indicator like "## CN-start" and "## CN-end"

## Remarks
Please let me know how to further improve.....
 
Have a blast!

## changes

08-10-2020	Initial version<br>
26-10-2020	Bugfixes<br>
25-06-2022	Added Escape funtion<br>
25-06-2022	Added special template for new issues<br>
17-08-2022	Made the Escape function configurable (config_inc.php & core/email_api.php)<br>
17-08-2022	Fixed minor lay-out issues in template_api.php<br>
14-03-2024	Added improved readme<br>
14-03-2024	Added sample email_api.php for MantisBT version 2.26<br>
12-04-2024	Added 4 fields to bug_note_template<br>
12-04-2024	Documented all fields for (and within) the bug_note_template<br>
12-04-2024 	Merged various updates/fixes from pkbarbiedoll (thanks for that)<br>
04-01-2025	Added prepared email-api.php for mantis 2.27<br>
