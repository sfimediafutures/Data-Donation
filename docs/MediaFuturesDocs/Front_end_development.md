# Front End development

##### This document locates files and folders used for front-end development, such as icons and content settings. Additionally, it provides some tips regarding the front-end process.

## Text content
Text content is edited by use of the *./osd2f/settings/default_content_settings.yaml*
file. Additionally, new tables for content can be added in *./osd2f/definitions/content_settings.py*.

The *default_content_settings.yaml* can render nordic letters, but must receive them in unicode format and 
wrapped in quotes. For example, if you want the page to display "Mappen må være i zip format", you will have
to translate the respective letters into unicode, leaving the sentence looking like so:
"Mappen m\u00E5 v\u00E6re i .zip format" 

Ideally a permanent resolution will be found where the entire page properly 
renders utf-8 and "æøåÆØÅ" can be written as-is in content documents. In the meantime, please refer to the unicode
table below.
```bash
æ : \u00E6
ø : \u00F8
å : \u00E5
Æ : \u00C6
Ø : \u00D8
Å : \u00C5
```
*Saving time when writing large paragraphs: Write the entire paragraph, then use (in pycharm) CTRL+R to find and 
replace all nordic letters. In larger texts this is faster than a hunt and peck method.* 

Troubleshooting: 
- If your nordic letters come out looking like this: Ã¦Ã¸Ã¥Ã†Ã˜Ã, you have forgotten to format them as unicode. Refer to above text.
- If you write the unicode translation of the letters and the site renders the code itself (eg. å as \u00E5), you may have forgotten to wrap the text in quotes (").

### Consent popup
The consent popup must be written by someone legally inclined, so that details and format are completely correct
and in line with industry standards. The text-prompt for the consent popup can be found within 
*../osd2f/settings/default_content_settings.yaml*, scrolling if required until the single indent "conset_popup" 
is found. Here, the title and lead of the consent popup can also be edited. The *points* tab is where the declaration
of consent itself should be written.

## Image content
Editing image content (adding, removing, changing images rendered on the website) 
is done in *./osd2f/static/*. Image files are located here and will be called on 
in *./osd2f/settings/default_content_settings.yaml*. Image tags in the aforementioned .yaml document
can call on both URLs and directory locations.

## Visualization components
Editing visualization components are done through Vue and are located in
the *./osd2f/javascript/visualization_components/* folder.

## Colors used

Hex colorcodes that are used at mediafutures.no (used here as well):
```
background: #231f20
accent: #7ae2c3
```
