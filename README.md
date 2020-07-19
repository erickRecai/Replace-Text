# Replace-Text
A userscript that replaces word or phrases that match regular expression rules.

Supports special text modification such as replacing an entire text instance if the regular expression rule set has "delete1" or "delete2" for the "new" text segment.

Additional functionality can be added with [Collapsable Toolbar](https://github.com/erickRecai/Collapsable-Toolbar) and [Script Options](https://github.com/erickRecai/Script-Options) scripts.

This script works mostly client side aside from the following external libraries:  
[jQuery](https://jquery.com/): Used to handle page events.  
[waitForKeyElements](https://greasyfork.org/en/scripts/5392-waitforkeyelements/code): Used to handle dynamic execution.

# Missed Text Nodes
If the script misses certain text instances, disabling either `rplt mrk chkd` in Script Options or set `markCheckedElements` to `0` in the code itself may catch the missed text.
#### Example of a missed text with `[/\w/g, "a"]`
![Missed Text Nodes](/instruction-images/ya-missed-text-nodes.png)
#### With `markCheckedElements` disabled
![With markCheckedElements Disabled](/instruction-images/yb-with-mark-checked-disabled.png)

# Installation
Requires a browser extension that enables userscripts to install this userscript. I personally use Tampermonkey but other extensions should work as well.  

[Tampermonkey for Chrome](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo?hl=en)  
[Tampermonkey for Firefox](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/)

To install this script specifically, just the `.user.js` file needs to downloaded.

# Instructions
Edit the script and add a rule set into the `replaceRules` array marked by `AB.`.  
A rule set consists of a regular expression and a string which can be a word or phrase.  
A regular expression can be as simple as a single word or a phrase between "/" and "/i" where the "i" tells the regular expression to ignore if any letters are capital or not.  
[More information about regular expressions can be found here.](https://www.w3schools.com/jsref/jsref_obj_regexp.asp)

### Basic Replace
Here is an example with a couple example rules.
```
[/commit/i, "dog"],
[/branch/i, "turtle"],
[/file/i, "birdie"],
```
![Basic Replace](/instruction-images/1a-basic-replace.png)

### Replacing all characters
Here is an example rule that replaces all "word" characters.  
`[/\w/g, "a"], //replaces all characters with "a".`
![Replacing all characters](/instruction-images/1b-replace-all-characters.png)

### Replacing by text nodes
Here is another example rule that replaces entire text instances.   
`[/(.|\W)+/i, "text"], //replaces all text instances with "text".`
![Replacing by text nodes](/instruction-images/1c-replace-by-text.png)

### Optional Script Options
With [Collapsable Toolbar](https://github.com/erickRecai/Collapsable-Toolbar) and [Script Options](https://github.com/erickRecai/Script-Options), you can change script options per site though you need to be on the site itself to change them. Otherwise, these options can be changed within the script in the section `BA. script options`.

![External Script Options](/instruction-images/2a-script-options.png)

How the scripts are ordered are generally the order that they run. There is a required order if you want everything to show up correctly should you want an onscreen user interface.
1. [Collapsable Toolbar](https://github.com/erickRecai/Collapsable-Toolbar)
2. [Script Options](https://github.com/erickRecai/Script-Options)
3. [Custom Rules](https://github.com/erickRecai/Custom-Rules)
4. Replace Text
5. [Filter, Highlight, & Delete](https://github.com/erickRecai/Filter-Highlight-Delete)
