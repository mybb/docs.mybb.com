---
layout: page
title:  "Changing Templates"
---

# Changing Templates

On this page, you will find how to make template edits in plugins.

### Here is how to make a basic template edit: 

For this example, we are going to edit the **index** template and add the variable **{$randomvar}** after the board statistics.

    function pluginname_activate() 
	{ 
		global $db; 
		require MYBB_ROOT.'/inc/adminfunctions_templates.php'; 
		find_replace_templatesets("index", '#'.preg_quote('{$boardstats}').'#', '{$boardstats}{$randomvar}'); 
	}
	
To reverse the template edit do this:

    function pluginname_deactivate() 
	{ 
		global $db; 
		require MYBB_ROOT.'/inc/adminfunctions_templates.php'; 
		find_replace_templatesets("index", '#'.preg_quote('{$randomvar}').'#', ''); 
	}