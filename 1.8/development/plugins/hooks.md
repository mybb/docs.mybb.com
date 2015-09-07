---
layout: page
title:  "Plugin Hooks"
categories: [plugins]
---

# MyBB Hooks

The following list was generated using [MyBB Hook Finder](https://github.com/euantorano/MyBB-Hook-Finder). The line numbers may be out of date.
<table>
<thead>
	<tr>
		<th colspan="3" class="tcat">MyBB Hooks</th>
	</tr>
</thead>
<tbody>
				
<tr class="file">
			<td colspan="3" class="tcat"><strong>File: </strong> admin/inc/class_form.php</td>
		</tr>
		<tr class="heading">
			<td>Hook</td>
			<td>Params</td>
			<td>Line</td>
		</tr>
		
<tr>
	<td>admin_form_output_submit_wrapper</td>
	<td>$buttons</td>
	<td>862</td>
</tr>

<tr>
	<td>admin_form_end</td>
	<td>$this</td>
	<td>887</td>
</tr>

<tr>
	<td>admin_formcontainer_output_row</td>
	<td>$pluginargs</td>
	<td>956</td>
</tr>

<tr>
	<td>admin_formcontainer_end</td>
	<td>$hook</td>
	<td>1049</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/inc/class_page.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_page_output_header</td>
	<td>$args</td>
	<td>81</td>
</tr>

<tr>
	<td>admin_page_output_footer</td>
	<td>$args</td>
	<td>206</td>
</tr>

<tr>
	<td>admin_page_show_login_start</td>
	<td>$args</td>
	<td>370</td>
</tr>

<tr>
	<td>admin_page_show_login_end</td>
	<td>$args</td>
	<td>506</td>
</tr>

<tr>
	<td>admin_page_output_tab_control_start</td>
	<td>$tabs</td>
	<td>800</td>
</tr>

<tr>
	<td>admin_page_output_tab_control_end</td>
	<td>$tabs</td>
	<td>819</td>
</tr>

<tr>
	<td>admin_page_output_nav_tabs_start</td>
	<td>$tabs</td>
	<td>831</td>
</tr>

<tr>
	<td>admin_page_output_nav_tabs_end</td>
	<td>$arguments</td>
	<td>864</td>
</tr>

<tr>
	<td>admin_page_output_confirm_action</td>
	<td>$args</td>
	<td>885</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/inc/functions_themes.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>update_theme_stylesheet_list_set_css_url</td>
	<td>$css_url</td>
	<td>1017</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/index.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tabs</td>
	<td>$modules</td>
	<td>697</td>
</tr>

<tr>
	<td>admin_load</td>
	<td></td>
	<td>764</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/attachment_types.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_attachment_types_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_attachment_types_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_attachment_types_add_commit</td>
	<td></td>
	<td>66</td>
</tr>

<tr>
	<td>admin_config_attachment_types_edit</td>
	<td></td>
	<td>151</td>
</tr>

<tr>
	<td>admin_config_attachment_types_edit_commit</td>
	<td></td>
	<td>185</td>
</tr>

<tr>
	<td>admin_config_attachment_types_delete</td>
	<td></td>
	<td>271</td>
</tr>

<tr>
	<td>admin_config_attachment_types_delete_commit</td>
	<td></td>
	<td>277</td>
</tr>

<tr>
	<td>admin_config_attachment_types_start</td>
	<td></td>
	<td>307</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/badwords.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_badwords_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_badwords_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_badwords_add_commit</td>
	<td></td>
	<td>67</td>
</tr>

<tr>
	<td>admin_config_badwords_delete</td>
	<td></td>
	<td>100</td>
</tr>

<tr>
	<td>admin_config_badwords_delete_commit</td>
	<td></td>
	<td>107</td>
</tr>

<tr>
	<td>admin_config_badwords_edit</td>
	<td></td>
	<td>135</td>
</tr>

<tr>
	<td>admin_config_badwords_edit_commit</td>
	<td></td>
	<td>161</td>
</tr>

<tr>
	<td>admin_config_badwords_start</td>
	<td></td>
	<td>219</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/banning.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_banning_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_banning_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_banning_add_commit</td>
	<td></td>
	<td>45</td>
</tr>

<tr>
	<td>admin_config_banning_delete</td>
	<td></td>
	<td>105</td>
</tr>

<tr>
	<td>admin_config_banning_delete_commit</td>
	<td></td>
	<td>131</td>
</tr>

<tr>
	<td>admin_config_banning_start</td>
	<td></td>
	<td>157</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/calendars.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_calendars_begin</td>
	<td></td>
	<td>32</td>
</tr>

<tr>
	<td>admin_config_calendars_add</td>
	<td></td>
	<td>36</td>
</tr>

<tr>
	<td>admin_config_calendars_add_commit</td>
	<td></td>
	<td>40</td>
</tr>

<tr>
	<td>admin_config_calendars_add_commit_start</td>
	<td></td>
	<td>68</td>
</tr>

<tr>
	<td>admin_config_calendars_add_commit_end</td>
	<td></td>
	<td>72</td>
</tr>

<tr>
	<td>admin_config_calendars_permissions</td>
	<td></td>
	<td>147</td>
</tr>

<tr>
	<td>admin_config_calendars_permissions_commit</td>
	<td></td>
	<td>187</td>
</tr>

<tr>
	<td>admin_config_calendars_edit</td>
	<td></td>
	<td>288</td>
</tr>

<tr>
	<td>admin_config_calendars_edit_commit</td>
	<td></td>
	<td>318</td>
</tr>

<tr>
	<td>admin_config_calendars_delete</td>
	<td></td>
	<td>388</td>
</tr>

<tr>
	<td>admin_config_calendars_delete_commit</td>
	<td></td>
	<td>403</td>
</tr>

<tr>
	<td>admin_config_calendars_update_order</td>
	<td></td>
	<td>424</td>
</tr>

<tr>
	<td>admin_config_calendars_update_order_commit</td>
	<td></td>
	<td>434</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/help_documents.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_help_documents_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_help_documents_add</td>
	<td></td>
	<td>24</td>
</tr>

<tr>
	<td>admin_config_help_documents_add_section</td>
	<td></td>
	<td>29</td>
</tr>

<tr>
	<td>admin_config_help_documents_add_section_commit</td>
	<td></td>
	<td>66</td>
</tr>

<tr>
	<td>admin_config_help_documents_add_page</td>
	<td></td>
	<td>128</td>
</tr>

<tr>
	<td>admin_config_help_documents_add_page_commit</td>
	<td></td>
	<td>177</td>
</tr>

<tr>
	<td>admin_config_help_documents_edit</td>
	<td></td>
	<td>252</td>
</tr>

<tr>
	<td>admin_config_help_documents_edit_section</td>
	<td></td>
	<td>260</td>
</tr>

<tr>
	<td>admin_config_help_documents_edit_section_commit</td>
	<td></td>
	<td>302</td>
</tr>

<tr>
	<td>admin_config_help_documents_edit_page</td>
	<td></td>
	<td>361</td>
</tr>

<tr>
	<td>admin_config_help_documents_edit_page_commit</td>
	<td></td>
	<td>410</td>
</tr>

<tr>
	<td>admin_config_help_documents_delete</td>
	<td></td>
	<td>491</td>
</tr>

<tr>
	<td>admin_config_help_documents_delete_section_commit</td>
	<td></td>
	<td>515</td>
</tr>

<tr>
	<td>admin_config_help_documents_delete_page_commit</td>
	<td></td>
	<td>541</td>
</tr>

<tr>
	<td>admin_config_help_documents_start</td>
	<td></td>
	<td>589</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/languages.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_languages_begin</td>
	<td></td>
	<td>21</td>
</tr>

<tr>
	<td>admin_config_languages_edit_properties</td>
	<td></td>
	<td>33</td>
</tr>

<tr>
	<td>admin_config_languages_edit_properties_commit</td>
	<td></td>
	<td>91</td>
</tr>

<tr>
	<td>admin_config_languages_quick_phrases</td>
	<td></td>
	<td>202</td>
</tr>

<tr>
	<td>admin_config_languages_edit</td>
	<td></td>
	<td>406</td>
</tr>

<tr>
	<td>admin_config_languages_edit_commit</td>
	<td></td>
	<td>475</td>
</tr>

<tr>
	<td>admin_config_languages_start</td>
	<td></td>
	<td>997</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/mod_tools.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_mod_tools_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_mod_tools_delete_post_tool</td>
	<td></td>
	<td>39</td>
</tr>

<tr>
	<td>admin_config_mod_tools_delete_post_tool_commit</td>
	<td></td>
	<td>46</td>
</tr>

<tr>
	<td>admin_config_mod_tools_delete_thread_tool</td>
	<td></td>
	<td>79</td>
</tr>

<tr>
	<td>admin_config_mod_tools_delete_thread_tool_commit</td>
	<td></td>
	<td>86</td>
</tr>

<tr>
	<td>admin_config_mod_tools_post_tools</td>
	<td></td>
	<td>103</td>
</tr>

<tr>
	<td>admin_config_mod_tools_edit_thread_tool</td>
	<td></td>
	<td>161</td>
</tr>

<tr>
	<td>admin_config_mod_tools_edit_thread_tool_commit</td>
	<td></td>
	<td>367</td>
</tr>

<tr>
	<td>admin_config_mod_tools_add_thread_tool</td>
	<td></td>
	<td>664</td>
</tr>

<tr>
	<td>admin_config_mod_tools_add_thread_tool_commit</td>
	<td></td>
	<td>873</td>
</tr>

<tr>
	<td>admin_config_mod_tools_edit_post_tool</td>
	<td></td>
	<td>1144</td>
</tr>

<tr>
	<td>admin_config_mod_tools_edit_post_tool_commit</td>
	<td></td>
	<td>1374</td>
</tr>

<tr>
	<td>admin_config_mod_tools_add_post_tool</td>
	<td></td>
	<td>1747</td>
</tr>

<tr>
	<td>admin_config_mod_tools_add_post_tool_commit</td>
	<td></td>
	<td>2013</td>
</tr>

<tr>
	<td>admin_config_mod_tools_start</td>
	<td></td>
	<td>2316</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/module_meta.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_menu</td>
	<td>$sub_menu</td>
	<td>43</td>
</tr>

<tr>
	<td>admin_config_action_handler</td>
	<td>$actions</td>
	<td>81</td>
</tr>

<tr>
	<td>admin_config_permissions</td>
	<td>$admin_permissions</td>
	<td>122</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/mycode.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_mycode_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_mycode_toggle_status</td>
	<td></td>
	<td>38</td>
</tr>

<tr>
	<td>admin_config_mycode_toggle_status_commit</td>
	<td></td>
	<td>54</td>
</tr>

<tr>
	<td>admin_config_mycode_xmlhttp_test_mycode_start</td>
	<td></td>
	<td>69</td>
</tr>

<tr>
	<td>admin_config_mycode_xmlhttp_test_mycode_end</td>
	<td></td>
	<td>80</td>
</tr>

<tr>
	<td>admin_config_mycode_add</td>
	<td></td>
	<td>88</td>
</tr>

<tr>
	<td>admin_config_mycode_add_commit</td>
	<td></td>
	<td>126</td>
</tr>

<tr>
	<td>admin_config_mycode_edit</td>
	<td></td>
	<td>215</td>
</tr>

<tr>
	<td>admin_config_mycode_edit_commit</td>
	<td></td>
	<td>251</td>
</tr>

<tr>
	<td>admin_config_mycode_delete</td>
	<td></td>
	<td>340</td>
</tr>

<tr>
	<td>admin_config_mycode_delete_commit</td>
	<td></td>
	<td>352</td>
</tr>

<tr>
	<td>admin_config_mycode_start</td>
	<td></td>
	<td>370</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/plugins.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_plugins_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_plugins_check</td>
	<td></td>
	<td>205</td>
</tr>

<tr>
	<td>admin_config_plugins_activate</td>
	<td></td>
	<td>382</td>
</tr>

<tr>
	<td>admin_config_plugins_deactivate</td>
	<td></td>
	<td>386</td>
</tr>

<tr>
	<td>admin_config_plugins_activate_commit</td>
	<td></td>
	<td>469</td>
</tr>

<tr>
	<td>admin_config_plugins_deactivate_commit</td>
	<td></td>
	<td>473</td>
</tr>

<tr>
	<td>admin_config_plugins_plugin_list</td>
	<td></td>
	<td>510</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/post_icons.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_post_icons_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_post_icons_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_post_icons_add_commit</td>
	<td></td>
	<td>46</td>
</tr>

<tr>
	<td>admin_config_post_icons_add_multiple</td>
	<td></td>
	<td>105</td>
</tr>

<tr>
	<td>admin_config_post_icons_add_multiple_commit</td>
	<td></td>
	<td>249</td>
</tr>

<tr>
	<td>admin_config_post_icons_edit</td>
	<td></td>
	<td>313</td>
</tr>

<tr>
	<td>admin_config_post_icons_edit_commit</td>
	<td></td>
	<td>334</td>
</tr>

<tr>
	<td>admin_config_post_icons_delete</td>
	<td></td>
	<td>402</td>
</tr>

<tr>
	<td>admin_config_post_icons_delete_commit</td>
	<td></td>
	<td>408</td>
</tr>

<tr>
	<td>admin_config_post_icons_start</td>
	<td></td>
	<td>426</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/profile_fields.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_profile_fields_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_profile_fields_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_profile_fields_add_commit</td>
	<td></td>
	<td>110</td>
</tr>

<tr>
	<td>admin_config_profile_fields_edit</td>
	<td></td>
	<td>348</td>
</tr>

<tr>
	<td>admin_config_profile_fields_edit_commit</td>
	<td></td>
	<td>427</td>
</tr>

<tr>
	<td>admin_config_profile_fields_delete</td>
	<td></td>
	<td>671</td>
</tr>

<tr>
	<td>admin_config_profile_fields_delete_commit</td>
	<td></td>
	<td>679</td>
</tr>

<tr>
	<td>admin_config_profile_fields_start</td>
	<td></td>
	<td>697</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/questions.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_questions_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_questions_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_questions_add_commit</td>
	<td></td>
	<td>48</td>
</tr>

<tr>
	<td>admin_config_questions_edit</td>
	<td></td>
	<td>110</td>
</tr>

<tr>
	<td>admin_config_questions_edit_commit</td>
	<td></td>
	<td>134</td>
</tr>

<tr>
	<td>admin_config_questions_delete</td>
	<td></td>
	<td>198</td>
</tr>

<tr>
	<td>admin_config_questions_delete_commit</td>
	<td></td>
	<td>205</td>
</tr>

<tr>
	<td>admin_config_questions_disable</td>
	<td></td>
	<td>230</td>
</tr>

<tr>
	<td>admin_config_questions_disable_commit</td>
	<td></td>
	<td>236</td>
</tr>

<tr>
	<td>admin_config_questions_enable</td>
	<td></td>
	<td>258</td>
</tr>

<tr>
	<td>admin_config_questions_enable_commit</td>
	<td></td>
	<td>264</td>
</tr>

<tr>
	<td>admin_config_questions_start</td>
	<td></td>
	<td>277</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/settings.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_settings_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_settings_addgroup</td>
	<td></td>
	<td>24</td>
</tr>

<tr>
	<td>admin_config_settings_addgroup_commit</td>
	<td></td>
	<td>57</td>
</tr>

<tr>
	<td>admin_config_settings_editgroup</td>
	<td></td>
	<td>133</td>
</tr>

<tr>
	<td>admin_config_settings_editgroup_commit</td>
	<td></td>
	<td>165</td>
</tr>

<tr>
	<td>admin_config_settings_deletegroup</td>
	<td></td>
	<td>241</td>
</tr>

<tr>
	<td>admin_config_settings_deletegroup_commit</td>
	<td></td>
	<td>251</td>
</tr>

<tr>
	<td>admin_config_settings_add</td>
	<td></td>
	<td>268</td>
</tr>

<tr>
	<td>admin_config_settings_add_commit</td>
	<td></td>
	<td>348</td>
</tr>

<tr>
	<td>admin_config_settings_edit</td>
	<td></td>
	<td>473</td>
</tr>

<tr>
	<td>admin_config_settings_edit_commit</td>
	<td></td>
	<td>551</td>
</tr>

<tr>
	<td>admin_config_settings_delete</td>
	<td></td>
	<td>697</td>
</tr>

<tr>
	<td>admin_config_settings_delete_commit</td>
	<td></td>
	<td>706</td>
</tr>

<tr>
	<td>admin_config_settings_manage</td>
	<td></td>
	<td>723</td>
</tr>

<tr>
	<td>admin_config_settings_manage_commit</td>
	<td></td>
	<td>748</td>
</tr>

<tr>
	<td>admin_config_settings_change</td>
	<td></td>
	<td>875</td>
</tr>

<tr>
	<td>admin_config_settings_change_commit</td>
	<td></td>
	<td>1015</td>
</tr>

<tr>
	<td>admin_config_settings_start</td>
	<td></td>
	<td>1426</td>
</tr>

<tr>
	<td>admin_settings_print_peekers</td>
	<td>$peekers</td>
	<td>1655</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/smilies.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_smilies_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_smilies_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_smilies_add_commit</td>
	<td></td>
	<td>79</td>
</tr>

<tr>
	<td>admin_config_smilies_edit</td>
	<td></td>
	<td>159</td>
</tr>

<tr>
	<td>admin_config_smilies_edit_commit</td>
	<td></td>
	<td>213</td>
</tr>

<tr>
	<td>admin_config_smilies_delete</td>
	<td></td>
	<td>289</td>
</tr>

<tr>
	<td>admin_config_smilies_delete_commit</td>
	<td></td>
	<td>296</td>
</tr>

<tr>
	<td>admin_config_smilies_add_multiple</td>
	<td></td>
	<td>313</td>
</tr>

<tr>
	<td>admin_config_smilies_add_multiple_step1</td>
	<td></td>
	<td>319</td>
</tr>

<tr>
	<td>admin_config_smilies_add_multiple_step2</td>
	<td></td>
	<td>438</td>
</tr>

<tr>
	<td>admin_config_smilies_add_multiple_commit</td>
	<td></td>
	<td>479</td>
</tr>

<tr>
	<td>admin_config_smilies_mass_edit</td>
	<td></td>
	<td>535</td>
</tr>

<tr>
	<td>admin_config_smilies_mass_edit_commit</td>
	<td></td>
	<td>582</td>
</tr>

<tr>
	<td>admin_config_smilies_start</td>
	<td></td>
	<td>683</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/spiders.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_spiders_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_config_spiders_add</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_config_spiders_add_commit</td>
	<td></td>
	<td>49</td>
</tr>

<tr>
	<td>admin_config_spiders_delete</td>
	<td></td>
	<td>133</td>
</tr>

<tr>
	<td>admin_config_spiders_delete_commit</td>
	<td></td>
	<td>140</td>
</tr>

<tr>
	<td>admin_config_spiders_edit</td>
	<td></td>
	<td>168</td>
</tr>

<tr>
	<td>admin_config_spiders_edit_commit</td>
	<td></td>
	<td>192</td>
</tr>

<tr>
	<td>admin_config_spiders_start</td>
	<td></td>
	<td>260</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/thread_prefixes.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_begin</td>
	<td></td>
	<td>32</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_add_prefix</td>
	<td></td>
	<td>36</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_add_prefix_commit</td>
	<td></td>
	<td>125</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_edit_prefix_start</td>
	<td></td>
	<td>238</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_edit_prefix_commit</td>
	<td></td>
	<td>325</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_delete_prefix</td>
	<td></td>
	<td>477</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_delete_thread_prefix_commit</td>
	<td></td>
	<td>487</td>
</tr>

<tr>
	<td>admin_config_thread_prefixes_start</td>
	<td></td>
	<td>506</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/config/warning.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_config_warning_begin</td>
	<td></td>
	<td>45</td>
</tr>

<tr>
	<td>admin_config_warning_add_level</td>
	<td></td>
	<td>49</td>
</tr>

<tr>
	<td>admin_config_warning_add_level_commit</td>
	<td></td>
	<td>97</td>
</tr>

<tr>
	<td>admin_config_warning_edit_level</td>
	<td></td>
	<td>218</td>
</tr>

<tr>
	<td>admin_config_warning_edit_level_commit</td>
	<td></td>
	<td>264</td>
</tr>

<tr>
	<td>admin_config_warning_delete_level</td>
	<td></td>
	<td>425</td>
</tr>

<tr>
	<td>admin_config_warning_delete_level_commit</td>
	<td></td>
	<td>432</td>
</tr>

<tr>
	<td>admin_config_warning_add_type</td>
	<td></td>
	<td>448</td>
</tr>

<tr>
	<td>admin_config_warning_add_type_commit</td>
	<td></td>
	<td>472</td>
</tr>

<tr>
	<td>admin_config_warning_edit_type</td>
	<td></td>
	<td>536</td>
</tr>

<tr>
	<td>admin_config_warning_edit_type_commit</td>
	<td></td>
	<td>558</td>
</tr>

<tr>
	<td>admin_config_warning_delete_type</td>
	<td></td>
	<td>638</td>
</tr>

<tr>
	<td>admin_config_warning_delete_type_commit</td>
	<td></td>
	<td>645</td>
</tr>

<tr>
	<td>admin_config_warning_levels</td>
	<td></td>
	<td>661</td>
</tr>

<tr>
	<td>admin_config_warning_start</td>
	<td></td>
	<td>731</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/forum/announcements.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_forum_announcements_begin</td>
	<td></td>
	<td>48</td>
</tr>

<tr>
	<td>admin_forum_announcements_add</td>
	<td></td>
	<td>52</td>
</tr>

<tr>
	<td>admin_forum_announcements_add_commit</td>
	<td></td>
	<td>172</td>
</tr>

<tr>
	<td>admin_forum_announcements_edit</td>
	<td></td>
	<td>433</td>
</tr>

<tr>
	<td>admin_forum_announcements_edit_commit</td>
	<td></td>
	<td>551</td>
</tr>

<tr>
	<td>admin_forum_announcements_delete</td>
	<td></td>
	<td>799</td>
</tr>

<tr>
	<td>admin_forum_announcements_delete_commit</td>
	<td></td>
	<td>805</td>
</tr>

<tr>
	<td>admin_forum_announcements_start</td>
	<td></td>
	<td>822</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/forum/attachments.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_forum_attachments_begin</td>
	<td></td>
	<td>40</td>
</tr>

<tr>
	<td>admin_forum_attachments_delete</td>
	<td></td>
	<td>44</td>
</tr>

<tr>
	<td>admin_forum_attachments_delete_commit</td>
	<td></td>
	<td>82</td>
</tr>

<tr>
	<td>admin_forum_attachments_stats</td>
	<td></td>
	<td>100</td>
</tr>

<tr>
	<td>admin_forum_attachments_delete_orphans</td>
	<td></td>
	<td>225</td>
</tr>

<tr>
	<td>admin_forum_attachments_delete_orphans_commit</td>
	<td></td>
	<td>269</td>
</tr>

<tr>
	<td>admin_forum_attachments_orphans</td>
	<td></td>
	<td>287</td>
</tr>

<tr>
	<td>admin_forum_attachments_step3</td>
	<td></td>
	<td>300</td>
</tr>

<tr>
	<td>admin_forum_attachments_orphans_step2</td>
	<td></td>
	<td>414</td>
</tr>

<tr>
	<td>admin_forum_attachments_orphans_step1</td>
	<td></td>
	<td>490</td>
</tr>

<tr>
	<td>admin_forum_attachments_start</td>
	<td></td>
	<td>614</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/forum/management.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_forum_management_begin</td>
	<td></td>
	<td>63</td>
</tr>

<tr>
	<td>admin_forum_management_copy</td>
	<td></td>
	<td>67</td>
</tr>

<tr>
	<td>admin_forum_management_copy_commit</td>
	<td></td>
	<td>171</td>
</tr>

<tr>
	<td>admin_forum_management_editmod</td>
	<td></td>
	<td>276</td>
</tr>

<tr>
	<td>admin_forum_management_editmod_commit</td>
	<td></td>
	<td>335</td>
</tr>

<tr>
	<td>admin_forum_management_clear_permission</td>
	<td></td>
	<td>437</td>
</tr>

<tr>
	<td>admin_forum_management_clear_permission_commit</td>
	<td></td>
	<td>458</td>
</tr>

<tr>
	<td>admin_forum_management_permissions</td>
	<td></td>
	<td>473</td>
</tr>

<tr>
	<td>admin_forum_management_permissions_commit</td>
	<td></td>
	<td>530</td>
</tr>

<tr>
	<td>admin_forum_management_permission_groups</td>
	<td>$groups</td>
	<td>733</td>
</tr>

<tr>
	<td>admin_forum_management_add</td>
	<td></td>
	<td>810</td>
</tr>

<tr>
	<td>admin_forum_management_add_commit</td>
	<td></td>
	<td>911</td>
</tr>

<tr>
	<td>admin_forum_management_edit</td>
	<td></td>
	<td>1311</td>
</tr>

<tr>
	<td>admin_forum_management_edit_commit</td>
	<td></td>
	<td>1473</td>
</tr>

<tr>
	<td>admin_forum_management_deletemod</td>
	<td></td>
	<td>1876</td>
</tr>

<tr>
	<td>admin_forum_management_deletemod_commit</td>
	<td></td>
	<td>1903</td>
</tr>

<tr>
	<td>admin_forum_management_delete</td>
	<td></td>
	<td>1946</td>
</tr>

<tr>
	<td>admin_forum_management_delete_commit</td>
	<td></td>
	<td>2003</td>
</tr>

<tr>
	<td>admin_forum_management_start</td>
	<td></td>
	<td>2034</td>
</tr>

<tr>
	<td>admin_forum_management_start_permissions_commit</td>
	<td></td>
	<td>2089</td>
</tr>

<tr>
	<td>admin_forum_management_start_moderators_commit</td>
	<td></td>
	<td>2182</td>
</tr>

<tr>
	<td>admin_forum_management_start_disporder_commit</td>
	<td></td>
	<td>2213</td>
</tr>

<tr>
	<td>admin_forum_management_start_graph_tabs</td>
	<td>$tabs</td>
	<td>2254</td>
</tr>

<tr>
	<td>admin_forum_management_start_graph</td>
	<td></td>
	<td>2638</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/forum/moderation_queue.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_begin</td>
	<td></td>
	<td>37</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_commit</td>
	<td></td>
	<td>42</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_threads_commit</td>
	<td></td>
	<td>78</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_posts_commit</td>
	<td></td>
	<td>116</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_attachments_commit</td>
	<td></td>
	<td>141</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_threads</td>
	<td></td>
	<td>160</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_posts</td>
	<td></td>
	<td>290</td>
</tr>

<tr>
	<td>admin_forum_moderation_queue_attachments</td>
	<td></td>
	<td>443</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/forum/module_meta.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_forum_menu</td>
	<td>$sub_menu</td>
	<td>30</td>
</tr>

<tr>
	<td>admin_forum_action_handler</td>
	<td>$actions</td>
	<td>55</td>
</tr>

<tr>
	<td>admin_forum_permissions</td>
	<td>$admin_permissions</td>
	<td>83</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/home/credits.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_home_credits_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_home_credits_start</td>
	<td></td>
	<td>42</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/home/index.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_home_index_begin</td>
	<td></td>
	<td>17</td>
</tr>

<tr>
	<td>admin_home_version_check_start</td>
	<td></td>
	<td>33</td>
</tr>

<tr>
	<td>admin_home_version_check</td>
	<td></td>
	<td>50</td>
</tr>

<tr>
	<td>admin_home_index_start</td>
	<td></td>
	<td>171</td>
</tr>

<tr>
	<td>admin_home_index_start_begin</td>
	<td></td>
	<td>182</td>
</tr>

<tr>
	<td>admin_home_index_output_message</td>
	<td></td>
	<td>298</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/home/module_meta.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_home_menu</td>
	<td>$sub_menu</td>
	<td>29</td>
</tr>

<tr>
	<td>admin_home_action_handler</td>
	<td>$actions</td>
	<td>63</td>
</tr>

<tr>
	<td>admin_home_menu_quick_access</td>
	<td>$sub_menu</td>
	<td>84</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/home/preferences.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_home_preferences_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_home_preferences_start</td>
	<td></td>
	<td>50</td>
</tr>

<tr>
	<td>admin_home_preferences_start_commit</td>
	<td></td>
	<td>92</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/style/module_meta.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_style_menu</td>
	<td>$sub_menu</td>
	<td>28</td>
</tr>

<tr>
	<td>admin_style_action_handler</td>
	<td>$actions</td>
	<td>50</td>
</tr>

<tr>
	<td>admin_style_permissions</td>
	<td>$admin_permissions</td>
	<td>76</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/style/templates.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_style_templates</td>
	<td></td>
	<td>108</td>
</tr>

<tr>
	<td>admin_style_templates_add_set</td>
	<td></td>
	<td>112</td>
</tr>

<tr>
	<td>admin_style_templates_add_set_commit</td>
	<td></td>
	<td>125</td>
</tr>

<tr>
	<td>admin_style_templates_add_template</td>
	<td></td>
	<td>175</td>
</tr>

<tr>
	<td>admin_style_templates_add_template_commit</td>
	<td></td>
	<td>216</td>
</tr>

<tr>
	<td>admin_style_templates_add_template_group</td>
	<td></td>
	<td>330</td>
</tr>

<tr>
	<td>admin_style_templates_add_template_group_commit</td>
	<td></td>
	<td>372</td>
</tr>

<tr>
	<td>admin_style_templates_edit_set</td>
	<td></td>
	<td>434</td>
</tr>

<tr>
	<td>admin_style_templates_edit_set_commit</td>
	<td></td>
	<td>449</td>
</tr>

<tr>
	<td>admin_style_templates_edit_template</td>
	<td></td>
	<td>512</td>
</tr>

<tr>
	<td>admin_style_templates_edit_template_commit_start</td>
	<td></td>
	<td>545</td>
</tr>

<tr>
	<td>admin_style_templates_edit_template_commit</td>
	<td></td>
	<td>569</td>
</tr>

<tr>
	<td>admin_style_templates_edit_template_group</td>
	<td></td>
	<td>758</td>
</tr>

<tr>
	<td>admin_style_templates_edit_template_group_commit</td>
	<td></td>
	<td>797</td>
</tr>

<tr>
	<td>admin_style_templates_search_replace</td>
	<td></td>
	<td>844</td>
</tr>

<tr>
	<td>admin_style_templates_search_replace_find</td>
	<td></td>
	<td>863</td>
</tr>

<tr>
	<td>admin_style_templates_search_replace_title</td>
	<td></td>
	<td>1043</td>
</tr>

<tr>
	<td>admin_style_templates_find_updated</td>
	<td></td>
	<td>1278</td>
</tr>

<tr>
	<td>admin_style_template_group_delete</td>
	<td></td>
	<td>1378</td>
</tr>

<tr>
	<td>admin_style_template_group_delete_commit</td>
	<td></td>
	<td>1387</td>
</tr>

<tr>
	<td>admin_style_templates_delete_set</td>
	<td></td>
	<td>1413</td>
</tr>

<tr>
	<td>admin_style_templates_delete_set_commit</td>
	<td></td>
	<td>1441</td>
</tr>

<tr>
	<td>admin_style_templates_delete_template</td>
	<td></td>
	<td>1479</td>
</tr>

<tr>
	<td>admin_style_templates_delete_template_commit</td>
	<td></td>
	<td>1486</td>
</tr>

<tr>
	<td>admin_style_templates_diff_report</td>
	<td></td>
	<td>1533</td>
</tr>

<tr>
	<td>admin_style_templates_diff_report_run</td>
	<td></td>
	<td>1558</td>
</tr>

<tr>
	<td>admin_style_templates_revert</td>
	<td></td>
	<td>1625</td>
</tr>

<tr>
	<td>admin_style_templates_revert_commit</td>
	<td></td>
	<td>1632</td>
</tr>

<tr>
	<td>admin_style_templates_set</td>
	<td></td>
	<td>1662</td>
</tr>

<tr>
	<td>admin_style_templates_start</td>
	<td></td>
	<td>1919</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/style/themes.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_style_themes_begin</td>
	<td></td>
	<td>135</td>
</tr>

<tr>
	<td>admin_style_themes_browse</td>
	<td></td>
	<td>139</td>
</tr>

<tr>
	<td>admin_style_themes_import</td>
	<td></td>
	<td>303</td>
</tr>

<tr>
	<td>admin_style_themes_import_commit</td>
	<td></td>
	<td>390</td>
</tr>

<tr>
	<td>admin_style_themes_export</td>
	<td></td>
	<td>529</td>
</tr>

<tr>
	<td>admin_style_themes_export_commit</td>
	<td></td>
	<td>667</td>
</tr>

<tr>
	<td>admin_style_themes_duplicate</td>
	<td></td>
	<td>747</td>
</tr>

<tr>
	<td>admin_style_themes_duplicate_commit</td>
	<td></td>
	<td>820</td>
</tr>

<tr>
	<td>admin_style_themes_add</td>
	<td></td>
	<td>888</td>
</tr>

<tr>
	<td>admin_style_themes_add_commit</td>
	<td></td>
	<td>911</td>
</tr>

<tr>
	<td>admin_style_themes_delete</td>
	<td></td>
	<td>967</td>
</tr>

<tr>
	<td>admin_style_themes_delete_commit</td>
	<td></td>
	<td>1032</td>
</tr>

<tr>
	<td>admin_style_themes_edit</td>
	<td></td>
	<td>1058</td>
</tr>

<tr>
	<td>admin_style_themes_edit_commit</td>
	<td></td>
	<td>1171</td>
</tr>

<tr>
	<td>admin_style_themes_stylesheet_properties</td>
	<td></td>
	<td>1625</td>
</tr>

<tr>
	<td>admin_style_themes_stylesheet_properties_commit</td>
	<td></td>
	<td>1752</td>
</tr>

<tr>
	<td>admin_style_themes_edit_stylesheet_simple</td>
	<td></td>
	<td>1999</td>
</tr>

<tr>
	<td>admin_style_themes_edit_stylesheet_simple_commit</td>
	<td></td>
	<td>2074</td>
</tr>

<tr>
	<td>admin_style_themes_edit_stylesheet_advanced</td>
	<td></td>
	<td>2263</td>
</tr>

<tr>
	<td>admin_style_themes_edit_stylesheet_advanced_commit</td>
	<td></td>
	<td>2309</td>
</tr>

<tr>
	<td>admin_style_themes_delete_stylesheet</td>
	<td></td>
	<td>2433</td>
</tr>

<tr>
	<td>admin_style_themes_delete_stylesheet_commit</td>
	<td></td>
	<td>2466</td>
</tr>

<tr>
	<td>admin_style_themes_add_stylesheet</td>
	<td></td>
	<td>2492</td>
</tr>

<tr>
	<td>admin_style_themes_add_stylesheet_commit</td>
	<td></td>
	<td>2594</td>
</tr>

<tr>
	<td>admin_style_themes_set_default</td>
	<td></td>
	<td>2911</td>
</tr>

<tr>
	<td>admin_style_themes_set_default_commit</td>
	<td></td>
	<td>2918</td>
</tr>

<tr>
	<td>admin_style_themes_force</td>
	<td></td>
	<td>2939</td>
</tr>

<tr>
	<td>admin_style_themes_force_commit</td>
	<td></td>
	<td>2953</td>
</tr>

<tr>
	<td>admin_style_themes_start</td>
	<td></td>
	<td>2973</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/adminlog.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_adminlog_begin</td>
	<td></td>
	<td>30</td>
</tr>

<tr>
	<td>admin_tools_adminlog_prune</td>
	<td></td>
	<td>40</td>
</tr>

<tr>
	<td>admin_tools_adminlog_prune_commit</td>
	<td></td>
	<td>67</td>
</tr>

<tr>
	<td>admin_tools_adminlog_start</td>
	<td></td>
	<td>155</td>
</tr>

<tr>
	<td>admin_tools_get_admin_log_action</td>
	<td>$plugin_array</td>
	<td>553</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/backupdb.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_backupdb_begin</td>
	<td></td>
	<td>55</td>
</tr>

<tr>
	<td>admin_tools_backupdb_dlbackup</td>
	<td></td>
	<td>65</td>
</tr>

<tr>
	<td>admin_tools_backupdb_dlbackup_commit</td>
	<td></td>
	<td>72</td>
</tr>

<tr>
	<td>admin_tools_backupdb_delete</td>
	<td></td>
	<td>104</td>
</tr>

<tr>
	<td>admin_tools_backupdb_delete_commit</td>
	<td></td>
	<td>112</td>
</tr>

<tr>
	<td>admin_tools_backupdb_backup</td>
	<td></td>
	<td>134</td>
</tr>

<tr>
	<td>admin_tools_backupdb_backup_disk_commit</td>
	<td></td>
	<td>285</td>
</tr>

<tr>
	<td>admin_tools_backupdb_backup_download_commit</td>
	<td></td>
	<td>296</td>
</tr>

<tr>
	<td>admin_tools_backupdb_start</td>
	<td></td>
	<td>418</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/cache.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_cache_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_tools_cache_view</td>
	<td></td>
	<td>29</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild</td>
	<td></td>
	<td>88</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild_commit</td>
	<td></td>
	<td>95</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild_commit</td>
	<td></td>
	<td>109</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild_commit</td>
	<td></td>
	<td>122</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild_commit</td>
	<td></td>
	<td>135</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild_commit</td>
	<td></td>
	<td>148</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild_all</td>
	<td></td>
	<td>171</td>
</tr>

<tr>
	<td>admin_tools_cache_rebuild_all_commit</td>
	<td></td>
	<td>201</td>
</tr>

<tr>
	<td>admin_tools_cache_start</td>
	<td></td>
	<td>220</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/file_verification.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_file_verification_begin</td>
	<td></td>
	<td>21</td>
</tr>

<tr>
	<td>admin_tools_file_verification_check</td>
	<td></td>
	<td>25</td>
</tr>

<tr>
	<td>admin_tools_file_verification_check_commit_start</td>
	<td></td>
	<td>79</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/mailerrors.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_mailerrors_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_tools_mailerrors_prune</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_tools_mailerrors_prune_delete_all_commit</td>
	<td></td>
	<td>30</td>
</tr>

<tr>
	<td>admin_tools_mailerrors_prune_commit</td>
	<td></td>
	<td>48</td>
</tr>

<tr>
	<td>admin_tools_mailerrors_view</td>
	<td></td>
	<td>67</td>
</tr>

<tr>
	<td>admin_tools_mailerrors_start</td>
	<td></td>
	<td>151</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/maillogs.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_maillogs_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_tools_maillogs_prune</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_tools_maillogs_prune_delete_all_commit</td>
	<td></td>
	<td>30</td>
</tr>

<tr>
	<td>admin_tools_maillogs_prune_commit</td>
	<td></td>
	<td>48</td>
</tr>

<tr>
	<td>admin_tools_maillogs_view</td>
	<td></td>
	<td>67</td>
</tr>

<tr>
	<td>admin_tools_maillogs_start</td>
	<td></td>
	<td>147</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/modlog.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_modlog_begin</td>
	<td></td>
	<td>30</td>
</tr>

<tr>
	<td>admin_tools_modlog_prune</td>
	<td></td>
	<td>34</td>
</tr>

<tr>
	<td>admin_tools_modlog_prune_commit</td>
	<td></td>
	<td>65</td>
</tr>

<tr>
	<td>admin_tools_modlog_start</td>
	<td></td>
	<td>129</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/module_meta.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_menu</td>
	<td>$sub_menu</td>
	<td>34</td>
</tr>

<tr>
	<td>admin_tools_action_handler</td>
	<td>$actions</td>
	<td>70</td>
</tr>

<tr>
	<td>admin_tools_menu_logs</td>
	<td>$sub_menu</td>
	<td>81</td>
</tr>

<tr>
	<td>admin_tools_permissions</td>
	<td>$admin_permissions</td>
	<td>129</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/optimizedb.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_optimizedb_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_tools_optimizedb_start</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>admin_tools_optimizedb_start_begin</td>
	<td></td>
	<td>48</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/php_info.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_php_info_phpinfo</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_tools_php_info_begin</td>
	<td></td>
	<td>30</td>
</tr>

<tr>
	<td>admin_tools_php_info_start</td>
	<td></td>
	<td>34</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/recount_rebuild.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_start</td>
	<td></td>
	<td>465</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_forum_counters</td>
	<td></td>
	<td>478</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_thread_counters</td>
	<td></td>
	<td>494</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_user_posts</td>
	<td></td>
	<td>510</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_user_threads</td>
	<td></td>
	<td>526</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_attachment_thumbs</td>
	<td></td>
	<td>542</td>
</tr>

<tr>
	<td>admin_tools_recount_recount_reputation</td>
	<td></td>
	<td>559</td>
</tr>

<tr>
	<td>admin_tools_recount_recount_warning</td>
	<td></td>
	<td>576</td>
</tr>

<tr>
	<td>admin_tools_recount_recount_private_messages</td>
	<td></td>
	<td>593</td>
</tr>

<tr>
	<td>admin_tools_recount_recount_referral</td>
	<td></td>
	<td>610</td>
</tr>

<tr>
	<td>admin_tools_recount_recount_thread_ratings</td>
	<td></td>
	<td>627</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_poll_counters</td>
	<td></td>
	<td>644</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_stats</td>
	<td></td>
	<td>661</td>
</tr>

<tr>
	<td>admin_tools_recount_rebuild_output_list</td>
	<td></td>
	<td>750</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/spamlog.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_spamlog_begin</td>
	<td></td>
	<td>29</td>
</tr>

<tr>
	<td>admin_tools_spamlog_prune</td>
	<td></td>
	<td>39</td>
</tr>

<tr>
	<td>admin_tools_spamlog_prune_commit</td>
	<td></td>
	<td>66</td>
</tr>

<tr>
	<td>admin_tools_spamlog_start</td>
	<td></td>
	<td>111</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/statistics.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_statistics_begin</td>
	<td></td>
	<td>35</td>
</tr>

<tr>
	<td>admin_tools_statistics_overall_begin</td>
	<td></td>
	<td>48</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/system_health.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_system_health_begin</td>
	<td></td>
	<td>37</td>
</tr>

<tr>
	<td>admin_tools_system_health_template_do_check_start</td>
	<td></td>
	<td>49</td>
</tr>

<tr>
	<td>admin_tools_system_health_template_do_check</td>
	<td></td>
	<td>66</td>
</tr>

<tr>
	<td>admin_tools_system_health_template_check</td>
	<td></td>
	<td>144</td>
</tr>

<tr>
	<td>admin_tools_system_health_utf8_conversion</td>
	<td></td>
	<td>178</td>
</tr>

<tr>
	<td>admin_tools_system_health_utf8_conversion_commit</td>
	<td></td>
	<td>370</td>
</tr>

<tr>
	<td>admin_tools_system_health_start</td>
	<td></td>
	<td>707</td>
</tr>

<tr>
	<td>admin_tools_system_health_output_chmod_list</td>
	<td></td>
	<td>966</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/tasks.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_tasks_begin</td>
	<td></td>
	<td>21</td>
</tr>

<tr>
	<td>admin_tools_tasks_add</td>
	<td></td>
	<td>68</td>
</tr>

<tr>
	<td>admin_tools_tasks_add_commit</td>
	<td></td>
	<td>142</td>
</tr>

<tr>
	<td>admin_tools_tasks_edit</td>
	<td></td>
	<td>260</td>
</tr>

<tr>
	<td>admin_tools_tasks_edit_commit</td>
	<td></td>
	<td>341</td>
</tr>

<tr>
	<td>admin_tools_tasks_delete</td>
	<td></td>
	<td>468</td>
</tr>

<tr>
	<td>admin_tools_tasks_delete_commit</td>
	<td></td>
	<td>478</td>
</tr>

<tr>
	<td>admin_tools_tasks_enable</td>
	<td></td>
	<td>514</td>
</tr>

<tr>
	<td>admin_tools_tasks_disable</td>
	<td></td>
	<td>518</td>
</tr>

<tr>
	<td>admin_tools_tasks_enable_commit</td>
	<td></td>
	<td>536</td>
</tr>

<tr>
	<td>admin_tools_tasks_enable_commit</td>
	<td></td>
	<td>556</td>
</tr>

<tr>
	<td>admin_tools_tasks_disable_commit</td>
	<td></td>
	<td>571</td>
</tr>

<tr>
	<td>admin_tools_tasks_run</td>
	<td></td>
	<td>594</td>
</tr>

<tr>
	<td>admin_tools_tasks_run_commit</td>
	<td></td>
	<td>608</td>
</tr>

<tr>
	<td>admin_tools_tasks_logs</td>
	<td></td>
	<td>619</td>
</tr>

<tr>
	<td>admin_tools_tasks_start</td>
	<td></td>
	<td>719</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/tools/warninglog.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_tools_warninglog_begin</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>admin_tools_warninglog_do_revoke</td>
	<td></td>
	<td>40</td>
</tr>

<tr>
	<td>admin_tools_warninglog_do_revoke_commit</td>
	<td></td>
	<td>72</td>
</tr>

<tr>
	<td>admin_tools_warninglog_view</td>
	<td></td>
	<td>107</td>
</tr>

<tr>
	<td>admin_tools_warninglog_start</td>
	<td></td>
	<td>237</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/admin_permissions.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_admin_permissions_begin</td>
	<td></td>
	<td>42</td>
</tr>

<tr>
	<td>admin_user_admin_permissions_delete</td>
	<td></td>
	<td>70</td>
</tr>

<tr>
	<td>admin_user_admin_permissions_delete_commit</td>
	<td></td>
	<td>78</td>
</tr>

<tr>
	<td>admin_user_admin_permissions_edit</td>
	<td></td>
	<td>119</td>
</tr>

<tr>
	<td>admin_user_admin_permissions_edit_commit</td>
	<td></td>
	<td>158</td>
</tr>

<tr>
	<td>admin_user_admin_permissions_group</td>
	<td></td>
	<td>312</td>
</tr>

<tr>
	<td>admin_user_admin_permissions_start</td>
	<td></td>
	<td>381</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/banning.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_banning_begin</td>
	<td></td>
	<td>51</td>
</tr>

<tr>
	<td>admin_user_banning_prune</td>
	<td></td>
	<td>78</td>
</tr>

<tr>
	<td>admin_user_banning_prune_commit</td>
	<td></td>
	<td>97</td>
</tr>

<tr>
	<td>admin_user_banning_lift</td>
	<td></td>
	<td>138</td>
</tr>

<tr>
	<td>admin_user_banning_lift_commit</td>
	<td></td>
	<td>149</td>
</tr>

<tr>
	<td>admin_user_banning_edit</td>
	<td></td>
	<td>181</td>
</tr>

<tr>
	<td>admin_user_banning_edit_commit</td>
	<td></td>
	<td>239</td>
</tr>

<tr>
	<td>admin_user_banning_start</td>
	<td></td>
	<td>308</td>
</tr>

<tr>
	<td>admin_user_banning_start_commit</td>
	<td></td>
	<td>401</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/group_promotions.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_group_promotions_begin</td>
	<td></td>
	<td>37</td>
</tr>

<tr>
	<td>admin_user_group_promotions_disable</td>
	<td></td>
	<td>61</td>
</tr>

<tr>
	<td>admin_user_group_promotions_disable_commit</td>
	<td></td>
	<td>69</td>
</tr>

<tr>
	<td>admin_user_group_promotions_delete</td>
	<td></td>
	<td>107</td>
</tr>

<tr>
	<td>admin_user_group_promotions_delete_commit</td>
	<td></td>
	<td>113</td>
</tr>

<tr>
	<td>admin_user_group_promotions_enable</td>
	<td></td>
	<td>150</td>
</tr>

<tr>
	<td>admin_user_group_promotions_enable_commit</td>
	<td></td>
	<td>156</td>
</tr>

<tr>
	<td>admin_user_group_promotions_edit</td>
	<td></td>
	<td>184</td>
</tr>

<tr>
	<td>admin_user_group_promotions_edit_commit</td>
	<td></td>
	<td>265</td>
</tr>

<tr>
	<td>admin_user_group_promotions_add</td>
	<td></td>
	<td>401</td>
</tr>

<tr>
	<td>admin_user_group_promotions_add_commit</td>
	<td></td>
	<td>484</td>
</tr>

<tr>
	<td>admin_user_group_promotions_logs</td>
	<td></td>
	<td>614</td>
</tr>

<tr>
	<td>admin_user_group_promotions_start</td>
	<td></td>
	<td>697</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/groups.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_groups_begin</td>
	<td></td>
	<td>116</td>
</tr>

<tr>
	<td>admin_user_groups_approve_join_request</td>
	<td></td>
	<td>135</td>
</tr>

<tr>
	<td>admin_user_groups_approve_join_request_commit</td>
	<td></td>
	<td>143</td>
</tr>

<tr>
	<td>admin_user_groups_deny_join_request</td>
	<td></td>
	<td>166</td>
</tr>

<tr>
	<td>admin_user_groups_deny_join_request_commit</td>
	<td></td>
	<td>171</td>
</tr>

<tr>
	<td>admin_user_groups_join_requests_start</td>
	<td></td>
	<td>188</td>
</tr>

<tr>
	<td>admin_user_groups_join_requests_commit</td>
	<td></td>
	<td>212</td>
</tr>

<tr>
	<td>admin_user_groups_join_requests_commit_end</td>
	<td></td>
	<td>217</td>
</tr>

<tr>
	<td>admin_user_groups_add_leader</td>
	<td></td>
	<td>325</td>
</tr>

<tr>
	<td>admin_user_groups_add_leader_commit</td>
	<td></td>
	<td>360</td>
</tr>

<tr>
	<td>admin_user_groups_leaders</td>
	<td></td>
	<td>391</td>
</tr>

<tr>
	<td>admin_user_groups_delete_leader</td>
	<td></td>
	<td>561</td>
</tr>

<tr>
	<td>admin_user_groups_delete_leader_commit</td>
	<td></td>
	<td>565</td>
</tr>

<tr>
	<td>admin_user_groups_delete_leader_commit_end</td>
	<td></td>
	<td>570</td>
</tr>

<tr>
	<td>admin_user_groups_edit_leader</td>
	<td></td>
	<td>605</td>
</tr>

<tr>
	<td>admin_user_groups_edit_leader_commit</td>
	<td></td>
	<td>615</td>
</tr>

<tr>
	<td>admin_user_groups_add</td>
	<td></td>
	<td>666</td>
</tr>

<tr>
	<td>admin_user_groups_add_commit</td>
	<td></td>
	<td>719</td>
</tr>

<tr>
	<td>admin_user_groups_add_commit_end</td>
	<td></td>
	<td>723</td>
</tr>

<tr>
	<td>admin_user_groups_edit</td>
	<td></td>
	<td>808</td>
</tr>

<tr>
	<td>admin_user_groups_edit_commit</td>
	<td></td>
	<td>953</td>
</tr>

<tr>
	<td>admin_user_groups_edit_graph_tabs</td>
	<td>$tabs</td>
	<td>1022</td>
</tr>

<tr>
	<td>admin_user_groups_edit_graph</td>
	<td></td>
	<td>1235</td>
</tr>

<tr>
	<td>admin_user_groups_delete</td>
	<td></td>
	<td>1266</td>
</tr>

<tr>
	<td>admin_user_groups_delete_commit</td>
	<td></td>
	<td>1284</td>
</tr>

<tr>
	<td>admin_user_groups_delete_commit_end</td>
	<td></td>
	<td>1313</td>
</tr>

<tr>
	<td>admin_user_groups_disporder</td>
	<td></td>
	<td>1335</td>
</tr>

<tr>
	<td>admin_user_groups_disporder_commit</td>
	<td></td>
	<td>1353</td>
</tr>

<tr>
	<td>admin_user_groups_start</td>
	<td></td>
	<td>1361</td>
</tr>

<tr>
	<td>admin_user_groups_start_commit</td>
	<td></td>
	<td>1372</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/mass_mail.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_mass_email</td>
	<td></td>
	<td>42</td>
</tr>

<tr>
	<td>admin_user_mass_email_edit_start</td>
	<td></td>
	<td>56</td>
</tr>

<tr>
	<td>admin_user_mass_email_edit_commit</td>
	<td></td>
	<td>193</td>
</tr>

<tr>
	<td>admin_user_mass_email_send_start</td>
	<td></td>
	<td>636</td>
</tr>

<tr>
	<td>admin_user_mass_email_send_finalize_commit</td>
	<td></td>
	<td>677</td>
</tr>

<tr>
	<td>admin_user_mass_email_send_define_commit</td>
	<td></td>
	<td>944</td>
</tr>

<tr>
	<td>admin_user_mass_email_send_review_commit</td>
	<td></td>
	<td>1055</td>
</tr>

<tr>
	<td>admin_user_mass_email_send_insert_commit</td>
	<td></td>
	<td>1165</td>
</tr>

<tr>
	<td>admin_user_mass_email_send_update_commit</td>
	<td></td>
	<td>1179</td>
</tr>

<tr>
	<td>admin_user_mass_email_preview_end</td>
	<td></td>
	<td>1398</td>
</tr>

<tr>
	<td>admin_user_mass_email_delete_start</td>
	<td></td>
	<td>1418</td>
</tr>

<tr>
	<td>admin_user_mass_email_delete_commit</td>
	<td></td>
	<td>1424</td>
</tr>

<tr>
	<td>admin_user_mass_email_preview_start</td>
	<td></td>
	<td>1464</td>
</tr>

<tr>
	<td>admin_user_mass_email_preview_end</td>
	<td></td>
	<td>1482</td>
</tr>

<tr>
	<td>admin_user_mass_email_resend_start</td>
	<td></td>
	<td>1505</td>
</tr>

<tr>
	<td>admin_user_mass_email_resend_end</td>
	<td></td>
	<td>1531</td>
</tr>

<tr>
	<td>admin_user_mass_email_cancel</td>
	<td></td>
	<td>1561</td>
</tr>

<tr>
	<td>admin_user_mass_email_archive_start</td>
	<td></td>
	<td>1575</td>
</tr>

<tr>
	<td>admin_user_mass_email_archive_end</td>
	<td></td>
	<td>1622</td>
</tr>

<tr>
	<td>admin_user_mass_email_start</td>
	<td></td>
	<td>1633</td>
</tr>

<tr>
	<td>admin_user_mass_email_end</td>
	<td></td>
	<td>1705</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/module_meta.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_menu</td>
	<td>$sub_menu</td>
	<td>33</td>
</tr>

<tr>
	<td>admin_user_action_handler</td>
	<td>$actions</td>
	<td>60</td>
</tr>

<tr>
	<td>admin_user_permissions</td>
	<td>$admin_permissions</td>
	<td>91</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/titles.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_titles_begin</td>
	<td></td>
	<td>33</td>
</tr>

<tr>
	<td>admin_user_titles_add</td>
	<td></td>
	<td>37</td>
</tr>

<tr>
	<td>admin_user_titles_add_commit</td>
	<td></td>
	<td>68</td>
</tr>

<tr>
	<td>admin_user_titles_edit</td>
	<td></td>
	<td>126</td>
</tr>

<tr>
	<td>admin_user_titles_edit_commit</td>
	<td></td>
	<td>155</td>
</tr>

<tr>
	<td>admin_user_titles_delete</td>
	<td></td>
	<td>224</td>
</tr>

<tr>
	<td>admin_user_titles_delete_commit</td>
	<td></td>
	<td>230</td>
</tr>

<tr>
	<td>admin_user_titles_start</td>
	<td></td>
	<td>248</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> admin/modules/user/users.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>admin_user_users_begin</td>
	<td></td>
	<td>143</td>
</tr>

<tr>
	<td>admin_user_users_coppa_activate</td>
	<td></td>
	<td>225</td>
</tr>

<tr>
	<td>admin_user_users_coppa_activate_commit</td>
	<td></td>
	<td>247</td>
</tr>

<tr>
	<td>admin_user_users_coppa_end</td>
	<td></td>
	<td>299</td>
</tr>

<tr>
	<td>admin_user_users_add</td>
	<td></td>
	<td>306</td>
</tr>

<tr>
	<td>admin_user_users_add_commit</td>
	<td></td>
	<td>359</td>
</tr>

<tr>
	<td>admin_user_users_edit</td>
	<td></td>
	<td>436</td>
</tr>

<tr>
	<td>admin_user_users_edit_commit_start</td>
	<td></td>
	<td>819</td>
</tr>

<tr>
	<td>admin_user_users_edit_commit</td>
	<td></td>
	<td>832</td>
</tr>

<tr>
	<td>admin_user_users_edit_graph_tabs</td>
	<td>$tabs</td>
	<td>956</td>
</tr>

<tr>
	<td>admin_user_users_edit_graph</td>
	<td></td>
	<td>1627</td>
</tr>

<tr>
	<td>admin_user_users_delete</td>
	<td></td>
	<td>1716</td>
</tr>

<tr>
	<td>admin_user_users_delete_commit</td>
	<td></td>
	<td>1720</td>
</tr>

<tr>
	<td>admin_user_users_delete_commit_end</td>
	<td></td>
	<td>1735</td>
</tr>

<tr>
	<td>admin_user_users_referrers</td>
	<td></td>
	<td>1759</td>
</tr>

<tr>
	<td>admin_user_users_ipaddresses</td>
	<td></td>
	<td>1809</td>
</tr>

<tr>
	<td>admin_user_users_merge</td>
	<td></td>
	<td>1889</td>
</tr>

<tr>
	<td>admin_user_users_merge_commit</td>
	<td></td>
	<td>2107</td>
</tr>

<tr>
	<td>admin_user_users_search</td>
	<td></td>
	<td>2217</td>
</tr>

<tr>
	<td>admin_user_users_search_commit</td>
	<td></td>
	<td>2291</td>
</tr>

<tr>
	<td>admin_user_users_inline</td>
	<td></td>
	<td>2357</td>
</tr>

<tr>
	<td>admin_user_users_start</td>
	<td></td>
	<td>3016</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> announcements.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>announcements_start</td>
	<td></td>
	<td>27</td>
</tr>

<tr>
	<td>announcements_end</td>
	<td></td>
	<td>123</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> archive/index.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>archive_start</td>
	<td></td>
	<td>19</td>
</tr>

<tr>
	<td>archive_announcement_start</td>
	<td></td>
	<td>67</td>
</tr>

<tr>
	<td>archive_announcement_end</td>
	<td></td>
	<td>72</td>
</tr>

<tr>
	<td>archive_thread_start</td>
	<td></td>
	<td>120</td>
</tr>

<tr>
	<td>archive_thread_post</td>
	<td></td>
	<td>221</td>
</tr>

<tr>
	<td>archive_thread_end</td>
	<td></td>
	<td>229</td>
</tr>

<tr>
	<td>archive_forum_start</td>
	<td></td>
	<td>268</td>
</tr>

<tr>
	<td>archive_forum_thread</td>
	<td></td>
	<td>365</td>
</tr>

<tr>
	<td>archive_forum_thread</td>
	<td></td>
	<td>403</td>
</tr>

<tr>
	<td>archive_forum_end</td>
	<td></td>
	<td>418</td>
</tr>

<tr>
	<td>archive_index_start</td>
	<td></td>
	<td>429</td>
</tr>

<tr>
	<td>archive_index_end</td>
	<td></td>
	<td>435</td>
</tr>

<tr>
	<td>archive_end</td>
	<td></td>
	<td>454</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> attachment.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>attachment_start</td>
	<td></td>
	<td>44</td>
</tr>

<tr>
	<td>attachment_end</td>
	<td></td>
	<td>99</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> calendar.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>calendar_start</td>
	<td></td>
	<td>55</td>
</tr>

<tr>
	<td>calendar_do_addevent_start</td>
	<td></td>
	<td>92</td>
</tr>

<tr>
	<td>calendar_do_addevent_end</td>
	<td></td>
	<td>211</td>
</tr>

<tr>
	<td>calendar_addevent_start</td>
	<td></td>
	<td>244</td>
</tr>

<tr>
	<td>calendar_addevent_end</td>
	<td></td>
	<td>550</td>
</tr>

<tr>
	<td>calendar_do_deleteevent_start</td>
	<td></td>
	<td>591</td>
</tr>

<tr>
	<td>calendar_do_deleteevent_end</td>
	<td></td>
	<td>597</td>
</tr>

<tr>
	<td>calendar_do_editevent_start</td>
	<td></td>
	<td>643</td>
</tr>

<tr>
	<td>calendar_do_editevent_end</td>
	<td></td>
	<td>760</td>
</tr>

<tr>
	<td>calendar_editevent_start</td>
	<td></td>
	<td>806</td>
</tr>

<tr>
	<td>calendar_editevent_end</td>
	<td></td>
	<td>1164</td>
</tr>

<tr>
	<td>calendar_move_start</td>
	<td></td>
	<td>1208</td>
</tr>

<tr>
	<td>calendar_move_end</td>
	<td></td>
	<td>1223</td>
</tr>

<tr>
	<td>calendar_do_move_start</td>
	<td></td>
	<td>1281</td>
</tr>

<tr>
	<td>calendar_do_move_end</td>
	<td></td>
	<td>1285</td>
</tr>

<tr>
	<td>calendar_approve_start</td>
	<td></td>
	<td>1329</td>
</tr>

<tr>
	<td>calendar_approve_end</td>
	<td></td>
	<td>1333</td>
</tr>

<tr>
	<td>calendar_unapprove_start</td>
	<td></td>
	<td>1377</td>
</tr>

<tr>
	<td>calendar_unapprove_end</td>
	<td></td>
	<td>1381</td>
</tr>

<tr>
	<td>calendar_event_start</td>
	<td></td>
	<td>1423</td>
</tr>

<tr>
	<td>calendar_event_end</td>
	<td></td>
	<td>1634</td>
</tr>

<tr>
	<td>calendar_dayview_start</td>
	<td></td>
	<td>1704</td>
</tr>

<tr>
	<td>calendar_dayview_end</td>
	<td></td>
	<td>1982</td>
</tr>

<tr>
	<td>calendar_weekview_start</td>
	<td></td>
	<td>2057</td>
</tr>

<tr>
	<td>calendar_weekview_end</td>
	<td></td>
	<td>2247</td>
</tr>

<tr>
	<td>calendar_main_view</td>
	<td></td>
	<td>2283</td>
</tr>

<tr>
	<td>calendar_end</td>
	<td></td>
	<td>2532</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> contact.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>contact_start</td>
	<td></td>
	<td>22</td>
</tr>

<tr>
	<td>contact_do_start</td>
	<td></td>
	<td>117</td>
</tr>

<tr>
	<td>contact_do_end</td>
	<td></td>
	<td>232</td>
</tr>

<tr>
	<td>contact_end</td>
	<td></td>
	<td>297</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> css.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>css_start</td>
	<td></td>
	<td>28</td>
</tr>

<tr>
	<td>css_end</td>
	<td></td>
	<td>35</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> editpost.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>editpost_start</td>
	<td></td>
	<td>28</td>
</tr>

<tr>
	<td>editpost_deletepost</td>
	<td></td>
	<td>251</td>
</tr>

<tr>
	<td>editpost_restorepost</td>
	<td></td>
	<td>378</td>
</tr>

<tr>
	<td>editpost_do_editpost_start</td>
	<td></td>
	<td>457</td>
</tr>

<tr>
	<td>editpost_do_editpost_end</td>
	<td></td>
	<td>540</td>
</tr>

<tr>
	<td>editpost_action_start</td>
	<td></td>
	<td>548</td>
</tr>

<tr>
	<td>editpost_end</td>
	<td></td>
	<td>927</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> forumdisplay.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>forumdisplay_start</td>
	<td></td>
	<td>37</td>
</tr>

<tr>
	<td>forumdisplay_announcement</td>
	<td></td>
	<td>823</td>
</tr>

<tr>
	<td>forumdisplay_get_threads</td>
	<td></td>
	<td>854</td>
</tr>

<tr>
	<td>forumdisplay_thread</td>
	<td></td>
	<td>998</td>
</tr>

<tr>
	<td>forumdisplay_thread_end</td>
	<td></td>
	<td>1315</td>
</tr>

<tr>
	<td>forumdisplay_end</td>
	<td></td>
	<td>1475</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> global.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>global_start</td>
	<td></td>
	<td>99</td>
</tr>

<tr>
	<td>global_intermediate</td>
	<td></td>
	<td>474</td>
</tr>

<tr>
	<td>global_end</td>
	<td></td>
	<td>1082</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/class_captcha.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>captcha_build_start</td>
	<td>$args</td>
	<td>112</td>
</tr>

<tr>
	<td>captcha_build_end</td>
	<td>$args</td>
	<td>182</td>
</tr>

<tr>
	<td>captcha_validate_start</td>
	<td>$this</td>
	<td>286</td>
</tr>

<tr>
	<td>captcha_validate_end</td>
	<td>$this</td>
	<td>423</td>
</tr>

<tr>
	<td>captcha_invalidate_end</td>
	<td>$this</td>
	<td>450</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/class_moderation.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>class_moderation_close_threads</td>
	<td>$tids</td>
	<td>31</td>
</tr>

<tr>
	<td>class_moderation_open_threads</td>
	<td>$tids</td>
	<td>67</td>
</tr>

<tr>
	<td>class_moderation_stick_threads</td>
	<td>$tids</td>
	<td>102</td>
</tr>

<tr>
	<td>class_moderation_unstick_threads</td>
	<td>$tids</td>
	<td>137</td>
</tr>

<tr>
	<td>class_moderation_remove_redirects</td>
	<td>$tid</td>
	<td>159</td>
</tr>

<tr>
	<td>class_moderation_delete_thread_start</td>
	<td>$tid</td>
	<td>189</td>
</tr>

<tr>
	<td>class_moderation_delete_thread</td>
	<td>$tid</td>
	<td>327</td>
</tr>

<tr>
	<td>class_moderation_delete_poll</td>
	<td>$pid</td>
	<td>349</td>
</tr>

<tr>
	<td>class_moderation_approve_threads</td>
	<td>$tids</td>
	<td>468</td>
</tr>

<tr>
	<td>class_moderation_unapprove_threads</td>
	<td>$tids</td>
	<td>618</td>
</tr>

<tr>
	<td>class_moderation_delete_post_start</td>
	<td>$pid</td>
	<td>663</td>
</tr>

<tr>
	<td>class_moderation_merge_posts</td>
	<td>$arguments</td>
	<td>944</td>
</tr>

<tr>
	<td>class_moderation_move_thread_redirect</td>
	<td>$arguments</td>
	<td>1044</td>
</tr>

<tr>
	<td>class_moderation_copy_thread</td>
	<td>$arguments</td>
	<td>1134</td>
</tr>

<tr>
	<td>class_moderation_move_simple</td>
	<td>$arguments</td>
	<td>1251</td>
</tr>

<tr>
	<td>class_moderation_merge_threads</td>
	<td>$arguments</td>
	<td>1524</td>
</tr>

<tr>
	<td>class_moderation_split_posts</td>
	<td>$arguments</td>
	<td>2127</td>
</tr>

<tr>
	<td>class_moderation_move_threads</td>
	<td>$arguments</td>
	<td>2363</td>
</tr>

<tr>
	<td>class_moderation_approve_posts</td>
	<td>$pids</td>
	<td>2522</td>
</tr>

<tr>
	<td>class_moderation_unapprove_posts</td>
	<td>$pids</td>
	<td>2690</td>
</tr>

<tr>
	<td>class_moderation_change_thread_subject</td>
	<td>$arguments</td>
	<td>2774</td>
</tr>

<tr>
	<td>class_moderation_expire_thread</td>
	<td>$arguments</td>
	<td>2803</td>
</tr>

<tr>
	<td>class_moderation_remove_thread_subscriptions</td>
	<td>$arguments</td>
	<td>3109</td>
</tr>

<tr>
	<td>class_moderation_apply_thread_prefix</td>
	<td>$arguments</td>
	<td>3145</td>
</tr>

<tr>
	<td>class_moderation_soft_delete_posts</td>
	<td>$pids</td>
	<td>3279</td>
</tr>

<tr>
	<td>class_moderation_restore_posts</td>
	<td>$pids</td>
	<td>3430</td>
</tr>

<tr>
	<td>class_moderation_restore_threads</td>
	<td>$tids</td>
	<td>3580</td>
</tr>

<tr>
	<td>class_moderation_soft_delete_threads</td>
	<td>$tids</td>
	<td>3736</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/class_parser.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>parse_message_start</td>
	<td>$message</td>
	<td>116</td>
</tr>

<tr>
	<td>parse_message</td>
	<td>$message</td>
	<td>187</td>
</tr>

<tr>
	<td>parse_message_end</td>
	<td>$message</td>
	<td>232</td>
</tr>

<tr>
	<td>text_parse_message</td>
	<td>$message</td>
	<td>1696</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/datahandlers/event.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>datahandler_event_validate</td>
	<td>$this</td>
	<td>430</td>
</tr>

<tr>
	<td>datahandler_event_insert</td>
	<td>$this</td>
	<td>522</td>
</tr>

<tr>
	<td>datahandler_event_insert_end</td>
	<td>$this</td>
	<td>533</td>
</tr>

<tr>
	<td>datahandler_event_update</td>
	<td>$this</td>
	<td>628</td>
</tr>

<tr>
	<td>datahandler_event_update_end</td>
	<td>$this</td>
	<td>638</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/datahandlers/login.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>datahandler_login_verify_password_start</td>
	<td>$args</td>
	<td>163</td>
</tr>

<tr>
	<td>datahandler_login_verify_password_end</td>
	<td>$args</td>
	<td>204</td>
</tr>

<tr>
	<td>datahandler_login_validate_start</td>
	<td>$this</td>
	<td>280</td>
</tr>

<tr>
	<td>datahandler_login_validate_end</td>
	<td>$this</td>
	<td>297</td>
</tr>

<tr>
	<td>datahandler_login_complete_start</td>
	<td>$this</td>
	<td>317</td>
</tr>

<tr>
	<td>datahandler_login_complete_end</td>
	<td>$this</td>
	<td>346</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/datahandlers/pm.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>datahandler_pm_validate</td>
	<td>$this</td>
	<td>479</td>
</tr>

<tr>
	<td>datahandler_pm_insert_updatedraft</td>
	<td>$this</td>
	<td>604</td>
</tr>

<tr>
	<td>datahandler_pm_insert</td>
	<td>$this</td>
	<td>683</td>
</tr>

<tr>
	<td>datahandler_pm_insert_savedcopy</td>
	<td>$this</td>
	<td>737</td>
</tr>

<tr>
	<td>datahandler_pm_insert_end</td>
	<td>$this</td>
	<td>751</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/datahandlers/post.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>datahandler_post_validate_post</td>
	<td>$this</td>
	<td>812</td>
</tr>

<tr>
	<td>datahandler_post_insert_merge</td>
	<td>$this</td>
	<td>1026</td>
</tr>

<tr>
	<td>datahandler_post_insert_post</td>
	<td>$this</td>
	<td>1065</td>
</tr>

<tr>
	<td>datahandler_post_insert_post</td>
	<td>$this</td>
	<td>1089</td>
</tr>

<tr>
	<td>datahandler_post_insert_subscribed</td>
	<td>$args</td>
	<td>1234</td>
</tr>

<tr>
	<td>datahandler_post_insert_post_end</td>
	<td>$this</td>
	<td>1285</td>
</tr>

<tr>
	<td>datahandler_post_validate_thread</td>
	<td>$this</td>
	<td>1345</td>
</tr>

<tr>
	<td>datahandler_post_insert_thread</td>
	<td>$this</td>
	<td>1440</td>
</tr>

<tr>
	<td>datahandler_post_insert_thread_post</td>
	<td>$this</td>
	<td>1455</td>
</tr>

<tr>
	<td>datahandler_post_insert_thread</td>
	<td>$this</td>
	<td>1481</td>
</tr>

<tr>
	<td>datahandler_post_insert_thread_post</td>
	<td>$this</td>
	<td>1499</td>
</tr>

<tr>
	<td>datahandler_post_insert_thread_end</td>
	<td>$this</td>
	<td>1731</td>
</tr>

<tr>
	<td>datahandler_post_update_thread</td>
	<td>$this</td>
	<td>1811</td>
</tr>

<tr>
	<td>datahandler_post_update</td>
	<td>$this</td>
	<td>1860</td>
</tr>

<tr>
	<td>datahandler_post_update_end</td>
	<td>$this</td>
	<td>1895</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/datahandlers/user.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>datahandler_user_validate</td>
	<td>$this</td>
	<td>1059</td>
</tr>

<tr>
	<td>datahandler_user_insert</td>
	<td>$this</td>
	<td>1187</td>
</tr>

<tr>
	<td>datahandler_user_insert_end</td>
	<td>$this</td>
	<td>1235</td>
</tr>

<tr>
	<td>datahandler_user_update</td>
	<td>$this</td>
	<td>1414</td>
</tr>

<tr>
	<td>datahandler_user_delete_start</td>
	<td>$this</td>
	<td>1517</td>
</tr>

<tr>
	<td>datahandler_user_delete_end</td>
	<td>$this</td>
	<td>1575</td>
</tr>

<tr>
	<td>datahandler_user_delete_content</td>
	<td>$this</td>
	<td>1612</td>
</tr>

<tr>
	<td>datahandler_user_delete_posts</td>
	<td>$this</td>
	<td>1680</td>
</tr>

<tr>
	<td>datahandler_user_clear_profile</td>
	<td>$this</td>
	<td>1750</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/datahandlers/warnings.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>datahandler_warnings_validate_warning</td>
	<td>$this</td>
	<td>268</td>
</tr>

<tr>
	<td>datahandler_warnings_insert_warning</td>
	<td>$this</td>
	<td>697</td>
</tr>

<tr>
	<td>datahandler_warnings_update_warning</td>
	<td>$this</td>
	<td>726</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/functions.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>pre_output_page</td>
	<td>$contents</td>
	<td>23</td>
</tr>

<tr>
	<td>post_output_page</td>
	<td></td>
	<td>98</td>
</tr>

<tr>
	<td>send_mail_queue_start</td>
	<td></td>
	<td>251</td>
</tr>

<tr>
	<td>send_mail_queue_end</td>
	<td></td>
	<td>277</td>
</tr>

<tr>
	<td>my_date</td>
	<td>$date</td>
	<td>506</td>
</tr>

<tr>
	<td>error</td>
	<td>$error</td>
	<td>759</td>
</tr>

<tr>
	<td>no_permission</td>
	<td></td>
	<td>848</td>
</tr>

<tr>
	<td>redirect</td>
	<td>$redirect_args</td>
	<td>917</td>
</tr>

<tr>
	<td>mycode_add_codebuttons</td>
	<td>$editor_lang_strings</td>
	<td>3184</td>
</tr>

<tr>
	<td>get_ip</td>
	<td>$ip_array</td>
	<td>3923</td>
</tr>

<tr>
	<td>mark_reports</td>
	<td>$arguments</td>
	<td>4604</td>
</tr>

<tr>
	<td>functions_fetch_ban_times</td>
	<td>$ban_times</td>
	<td>7123</td>
</tr>

<tr>
	<td>copy_file_to_cdn_end</td>
	<td>$hook_args</td>
	<td>8319</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/functions_forumlist.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>build_forumbits_forum</td>
	<td>$forum</td>
	<td>60</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/functions_online.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>fetch_wol_activity_end</td>
	<td>$user_activity</td>
	<td>562</td>
</tr>

<tr>
	<td>build_friendly_wol_location_end</td>
	<td>$plugin_array</td>
	<td>1103</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/functions_post.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>postbit_prev</td>
	<td>$post</td>
	<td>776</td>
</tr>

<tr>
	<td>postbit_pm</td>
	<td>$post</td>
	<td>779</td>
</tr>

<tr>
	<td>postbit_announcement</td>
	<td>$post</td>
	<td>782</td>
</tr>

<tr>
	<td>postbit</td>
	<td>$post</td>
	<td>785</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/functions_posting.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>parse_quoted_message</td>
	<td>$quoted_post</td>
	<td>209</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/functions_upload.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>remove_attachment_do_delete</td>
	<td>$attachment</td>
	<td>35</td>
</tr>

<tr>
	<td>remove_attachments_do_delete</td>
	<td>$attachment</td>
	<td>113</td>
</tr>

<tr>
	<td>remove_avatars_do_delete</td>
	<td>$file</td>
	<td>165</td>
</tr>

<tr>
	<td>upload_avatar_end</td>
	<td>$ret</td>
	<td>335</td>
</tr>

<tr>
	<td>upload_attachment_start</td>
	<td>$attachment</td>
	<td>390</td>
</tr>

<tr>
	<td>upload_attachment_thumb_start</td>
	<td>$attacharray</td>
	<td>587</td>
</tr>

<tr>
	<td>upload_attachment_do_insert</td>
	<td>$attacharray</td>
	<td>609</td>
</tr>

<tr>
	<td>delete_uploaded_file</td>
	<td>$hook_params</td>
	<td>677</td>
</tr>

<tr>
	<td>delete_upload_directory</td>
	<td>$hook_params</td>
	<td>711</td>
</tr>

<tr>
	<td>upload_file_end</td>
	<td>$upload</td>
	<td>759</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/functions_user.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>password_changed</td>
	<td></td>
	<td>164</td>
</tr>

<tr>
	<td>usercp_menu</td>
	<td></td>
	<td>399</td>
</tr>

<tr>
	<td>usercp_menu_built</td>
	<td></td>
	<td>404</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/backupdb.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_backupdb</td>
	<td>$args</td>
	<td>59</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/checktables.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_checktables</td>
	<td>$task</td>
	<td>77</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/dailycleanup.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_dailycleanup_start</td>
	<td>$args</td>
	<td>31</td>
</tr>

<tr>
	<td>task_dailycleanup_end</td>
	<td>$args</td>
	<td>70</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/delayedmoderation.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_delayedmoderation</td>
	<td>$args</td>
	<td>31</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/hourlycleanup.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_hourlycleanup</td>
	<td>$args</td>
	<td>28</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/logcleanup.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_logcleanup</td>
	<td>$task</td>
	<td>59</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/massmail.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_massmail</td>
	<td>$args</td>
	<td>33</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/promotions.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_promotions</td>
	<td>$args</td>
	<td>167</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/threadviews.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_threadviews</td>
	<td>$task</td>
	<td>31</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/usercleanup.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_usercleanup</td>
	<td>$task</td>
	<td>70</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> inc/tasks/userpruning.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>task_userpruning</td>
	<td>$args</td>
	<td>87</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> index.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>index_start</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>index_end</td>
	<td></td>
	<td>387</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> managegroup.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>managegroup_do_add_start</td>
	<td></td>
	<td>58</td>
</tr>

<tr>
	<td>managegroup_do_add_end</td>
	<td></td>
	<td>73</td>
</tr>

<tr>
	<td>managegroup_do_invite_start</td>
	<td></td>
	<td>96</td>
</tr>

<tr>
	<td>managegroup_do_invite_end</td>
	<td></td>
	<td>144</td>
</tr>

<tr>
	<td>managegroup_do_joinrequests_start</td>
	<td></td>
	<td>169</td>
</tr>

<tr>
	<td>managegroup_do_joinrequests_end</td>
	<td></td>
	<td>194</td>
</tr>

<tr>
	<td>managegroup_joinrequests_start</td>
	<td></td>
	<td>201</td>
</tr>

<tr>
	<td>managegroup_joinrequests_end</td>
	<td></td>
	<td>224</td>
</tr>

<tr>
	<td>managegroup_do_manageusers_start</td>
	<td></td>
	<td>239</td>
</tr>

<tr>
	<td>managegroup_do_manageusers_end</td>
	<td></td>
	<td>253</td>
</tr>

<tr>
	<td>managegroup_start</td>
	<td></td>
	<td>259</td>
</tr>

<tr>
	<td>managegroup_end</td>
	<td></td>
	<td>423</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> member.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>member_do_register_start</td>
	<td></td>
	<td>90</td>
</tr>

<tr>
	<td>member_do_register_end</td>
	<td></td>
	<td>398</td>
</tr>

<tr>
	<td>member_do_register_end</td>
	<td></td>
	<td>432</td>
</tr>

<tr>
	<td>member_do_register_end</td>
	<td></td>
	<td>456</td>
</tr>

<tr>
	<td>member_do_register_end</td>
	<td></td>
	<td>544</td>
</tr>

<tr>
	<td>member_do_register_end</td>
	<td></td>
	<td>658</td>
</tr>

<tr>
	<td>member_do_register_end</td>
	<td></td>
	<td>666</td>
</tr>

<tr>
	<td>member_coppa_form</td>
	<td></td>
	<td>680</td>
</tr>

<tr>
	<td>member_register_coppa</td>
	<td></td>
	<td>749</td>
</tr>

<tr>
	<td>member_register_agreement</td>
	<td></td>
	<td>773</td>
</tr>

<tr>
	<td>member_register_start</td>
	<td></td>
	<td>780</td>
</tr>

<tr>
	<td>member_register_end</td>
	<td></td>
	<td>1287</td>
</tr>

<tr>
	<td>member_activate_start</td>
	<td></td>
	<td>1296</td>
</tr>

<tr>
	<td>member_activate_emailupdated</td>
	<td></td>
	<td>1362</td>
</tr>

<tr>
	<td>member_activate_emailactivated</td>
	<td></td>
	<td>1372</td>
</tr>

<tr>
	<td>member_activate_accountactivated</td>
	<td></td>
	<td>1378</td>
</tr>

<tr>
	<td>member_activate_form</td>
	<td></td>
	<td>1385</td>
</tr>

<tr>
	<td>member_resendactivation</td>
	<td></td>
	<td>1401</td>
</tr>

<tr>
	<td>member_resendactivation_end</td>
	<td></td>
	<td>1420</td>
</tr>

<tr>
	<td>member_do_resendactivation_start</td>
	<td></td>
	<td>1428</td>
</tr>

<tr>
	<td>member_do_resendactivation_end</td>
	<td></td>
	<td>1491</td>
</tr>

<tr>
	<td>member_lostpw</td>
	<td></td>
	<td>1499</td>
</tr>

<tr>
	<td>member_do_lostpw_start</td>
	<td></td>
	<td>1507</td>
</tr>

<tr>
	<td>member_do_lostpw_end</td>
	<td></td>
	<td>1553</td>
</tr>

<tr>
	<td>member_resetpassword_start</td>
	<td></td>
	<td>1560</td>
</tr>

<tr>
	<td>member_resetpassword_process</td>
	<td></td>
	<td>1618</td>
</tr>

<tr>
	<td>member_resetpassword_reset</td>
	<td></td>
	<td>1624</td>
</tr>

<tr>
	<td>member_resetpassword_form</td>
	<td></td>
	<td>1630</td>
</tr>

<tr>
	<td>member_do_login_start</td>
	<td></td>
	<td>1664</td>
</tr>

<tr>
	<td>member_do_login_end</td>
	<td></td>
	<td>1727</td>
</tr>

<tr>
	<td>member_do_login_end</td>
	<td></td>
	<td>1750</td>
</tr>

<tr>
	<td>member_login</td>
	<td></td>
	<td>1755</td>
</tr>

<tr>
	<td>member_login_end</td>
	<td></td>
	<td>1843</td>
</tr>

<tr>
	<td>member_logout_start</td>
	<td></td>
	<td>1851</td>
</tr>

<tr>
	<td>member_logout_end</td>
	<td></td>
	<td>1880</td>
</tr>

<tr>
	<td>member_viewnotes</td>
	<td></td>
	<td>1905</td>
</tr>

<tr>
	<td>member_profile_start</td>
	<td></td>
	<td>1914</td>
</tr>

<tr>
	<td>member_profile_end</td>
	<td></td>
	<td>2697</td>
</tr>

<tr>
	<td>member_do_emailuser_start</td>
	<td></td>
	<td>2708</td>
</tr>

<tr>
	<td>member_do_emailuser_end</td>
	<td></td>
	<td>2869</td>
</tr>

<tr>
	<td>member_emailuser_start</td>
	<td></td>
	<td>2881</td>
</tr>

<tr>
	<td>member_emailuser_end</td>
	<td></td>
	<td>3013</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> memberlist.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>memberlist_start</td>
	<td></td>
	<td>27</td>
</tr>

<tr>
	<td>memberlist_search</td>
	<td></td>
	<td>39</td>
</tr>

<tr>
	<td>memberlist_intermediate</td>
	<td></td>
	<td>265</td>
</tr>

<tr>
	<td>memberlist_user</td>
	<td>$user</td>
	<td>311</td>
</tr>

<tr>
	<td>memberlist_end</td>
	<td></td>
	<td>436</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> misc.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>misc_start</td>
	<td></td>
	<td>25</td>
</tr>

<tr>
	<td>misc_markread_forum</td>
	<td></td>
	<td>79</td>
</tr>

<tr>
	<td>misc_markread_end</td>
	<td></td>
	<td>94</td>
</tr>

<tr>
	<td>misc_clearpass</td>
	<td></td>
	<td>102</td>
</tr>

<tr>
	<td>misc_rules_start</td>
	<td></td>
	<td>119</td>
</tr>

<tr>
	<td>misc_rules_end</td>
	<td></td>
	<td>156</td>
</tr>

<tr>
	<td>misc_do_helpsearch_start</td>
	<td></td>
	<td>165</td>
</tr>

<tr>
	<td>misc_do_helpsearch_process</td>
	<td></td>
	<td>237</td>
</tr>

<tr>
	<td>misc_do_helpsearch_end</td>
	<td></td>
	<td>241</td>
</tr>

<tr>
	<td>misc_helpresults_start</td>
	<td></td>
	<td>260</td>
</tr>

<tr>
	<td>misc_helpresults_bit</td>
	<td></td>
	<td>345</td>
</tr>

<tr>
	<td>misc_helpresults_end</td>
	<td></td>
	<td>355</td>
</tr>

<tr>
	<td>misc_help_helpdoc_start</td>
	<td></td>
	<td>382</td>
</tr>

<tr>
	<td>misc_help_helpdoc_end</td>
	<td></td>
	<td>421</td>
</tr>

<tr>
	<td>misc_help_section_start</td>
	<td></td>
	<td>433</td>
</tr>

<tr>
	<td>misc_help_section_end</td>
	<td></td>
	<td>507</td>
</tr>

<tr>
	<td>misc_buddypopup_start</td>
	<td></td>
	<td>515</td>
</tr>

<tr>
	<td>misc_buddypopup_end</td>
	<td></td>
	<td>608</td>
</tr>

<tr>
	<td>misc_syndication_start</td>
	<td></td>
	<td>838</td>
</tr>

<tr>
	<td>misc_syndication_end</td>
	<td></td>
	<td>939</td>
</tr>

<tr>
	<td>misc_clearcookies</td>
	<td></td>
	<td>948</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> modcp.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>modcp_nav</td>
	<td></td>
	<td>261</td>
</tr>

<tr>
	<td>modcp_start</td>
	<td></td>
	<td>275</td>
</tr>

<tr>
	<td>modcp_do_reports</td>
	<td></td>
	<td>301</td>
</tr>

<tr>
	<td>modcp_reports_start</td>
	<td></td>
	<td>381</td>
</tr>

<tr>
	<td>modcp_reports_intermediate</td>
	<td></td>
	<td>492</td>
</tr>

<tr>
	<td>modcp_reports_report</td>
	<td></td>
	<td>568</td>
</tr>

<tr>
	<td>modcp_reports_end</td>
	<td></td>
	<td>573</td>
</tr>

<tr>
	<td>modcp_allreports_start</td>
	<td></td>
	<td>669</td>
</tr>

<tr>
	<td>modcp_allreports_report</td>
	<td></td>
	<td>741</td>
</tr>

<tr>
	<td>modcp_allreports_end</td>
	<td></td>
	<td>746</td>
</tr>

<tr>
	<td>modcp_modlogs_start</td>
	<td></td>
	<td>809</td>
</tr>

<tr>
	<td>modcp_modlogs_filter</td>
	<td></td>
	<td>938</td>
</tr>

<tr>
	<td>modcp_do_delete_announcement</td>
	<td></td>
	<td>998</td>
</tr>

<tr>
	<td>modcp_delete_announcement</td>
	<td></td>
	<td>1030</td>
</tr>

<tr>
	<td>modcp_do_new_announcement_start</td>
	<td></td>
	<td>1157</td>
</tr>

<tr>
	<td>modcp_do_new_announcement_end</td>
	<td></td>
	<td>1183</td>
</tr>

<tr>
	<td>modcp_new_announcement</td>
	<td></td>
	<td>1393</td>
</tr>

<tr>
	<td>modcp_do_edit_announcement_start</td>
	<td></td>
	<td>1526</td>
</tr>

<tr>
	<td>modcp_do_edit_announcement_end</td>
	<td></td>
	<td>1552</td>
</tr>

<tr>
	<td>modcp_edit_announcement</td>
	<td></td>
	<td>1793</td>
</tr>

<tr>
	<td>modcp_announcements</td>
	<td></td>
	<td>1865</td>
</tr>

<tr>
	<td>modcp_do_modqueue_start</td>
	<td></td>
	<td>1884</td>
</tr>

<tr>
	<td>modcp_do_modqueue_end</td>
	<td></td>
	<td>1933</td>
</tr>

<tr>
	<td>modcp_do_modqueue_end</td>
	<td></td>
	<td>1981</td>
</tr>

<tr>
	<td>modcp_do_modqueue_end</td>
	<td></td>
	<td>2012</td>
</tr>

<tr>
	<td>modcp_modqueue_threads_end</td>
	<td></td>
	<td>2127</td>
</tr>

<tr>
	<td>modcp_modqueue_posts_end</td>
	<td></td>
	<td>2248</td>
</tr>

<tr>
	<td>modcp_modqueue_attachments_end</td>
	<td></td>
	<td>2364</td>
</tr>

<tr>
	<td>modcp_modqueue_end</td>
	<td></td>
	<td>2389</td>
</tr>

<tr>
	<td>modcp_do_editprofile_start</td>
	<td></td>
	<td>2418</td>
</tr>

<tr>
	<td>modcp_do_editprofile_update</td>
	<td></td>
	<td>2633</td>
</tr>

<tr>
	<td>modcp_do_editprofile_end</td>
	<td></td>
	<td>2643</td>
</tr>

<tr>
	<td>modcp_editprofile_start</td>
	<td></td>
	<td>2831</td>
</tr>

<tr>
	<td>modcp_editprofile_end</td>
	<td></td>
	<td>3165</td>
</tr>

<tr>
	<td>modcp_finduser_start</td>
	<td></td>
	<td>3272</td>
</tr>

<tr>
	<td>modcp_finduser_end</td>
	<td></td>
	<td>3309</td>
</tr>

<tr>
	<td>modcp_warninglogs_start</td>
	<td></td>
	<td>3427</td>
</tr>

<tr>
	<td>modcp_warninglogs_end</td>
	<td></td>
	<td>3524</td>
</tr>

<tr>
	<td>modcp_ipsearch_posts_start</td>
	<td></td>
	<td>3568</td>
</tr>

<tr>
	<td>modcp_ipsearch_users_start</td>
	<td></td>
	<td>3592</td>
</tr>

<tr>
	<td>modcp_ipsearch_end</td>
	<td></td>
	<td>3802</td>
</tr>

<tr>
	<td>modcp_iplookup_end</td>
	<td></td>
	<td>3845</td>
</tr>

<tr>
	<td>modcp_banning_start</td>
	<td></td>
	<td>3903</td>
</tr>

<tr>
	<td>modcp_banning</td>
	<td></td>
	<td>3978</td>
</tr>

<tr>
	<td>modcp_liftban_start</td>
	<td></td>
	<td>4008</td>
</tr>

<tr>
	<td>modcp_liftban_end</td>
	<td></td>
	<td>4025</td>
</tr>

<tr>
	<td>modcp_do_banuser_start</td>
	<td></td>
	<td>4118</td>
</tr>

<tr>
	<td>modcp_do_banuser_end</td>
	<td></td>
	<td>4189</td>
</tr>

<tr>
	<td>modcp_banuser_start</td>
	<td></td>
	<td>4226</td>
</tr>

<tr>
	<td>modcp_banuser_end</td>
	<td></td>
	<td>4356</td>
</tr>

<tr>
	<td>modcp_do_modnotes_start</td>
	<td></td>
	<td>4367</td>
</tr>

<tr>
	<td>modcp_do_modnotes_end</td>
	<td></td>
	<td>4375</td>
</tr>

<tr>
	<td>modcp_end</td>
	<td></td>
	<td>4681</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> moderation.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>moderation_start</td>
	<td></td>
	<td>31</td>
</tr>

<tr>
	<td>moderation_cancel_delayedmoderation</td>
	<td></td>
	<td>131</td>
</tr>

<tr>
	<td>moderation_do_delayedmoderation</td>
	<td></td>
	<td>291</td>
</tr>

<tr>
	<td>moderation_delayedmoderation</td>
	<td></td>
	<td>574</td>
</tr>

<tr>
	<td>moderation_stick</td>
	<td></td>
	<td>619</td>
</tr>

<tr>
	<td>moderation_removeredirects</td>
	<td></td>
	<td>652</td>
</tr>

<tr>
	<td>moderation_deletethread</td>
	<td></td>
	<td>673</td>
</tr>

<tr>
	<td>moderation_do_deletethread</td>
	<td></td>
	<td>693</td>
</tr>

<tr>
	<td>moderation_deletepoll</td>
	<td></td>
	<td>720</td>
</tr>

<tr>
	<td>moderation_do_deletepoll</td>
	<td></td>
	<td>757</td>
</tr>

<tr>
	<td>moderation_approvethread</td>
	<td></td>
	<td>779</td>
</tr>

<tr>
	<td>moderation_unapprovethread</td>
	<td></td>
	<td>801</td>
</tr>

<tr>
	<td>moderation_restorethread</td>
	<td></td>
	<td>823</td>
</tr>

<tr>
	<td>moderation_softdeletethread</td>
	<td></td>
	<td>845</td>
</tr>

<tr>
	<td>moderation_move</td>
	<td></td>
	<td>863</td>
</tr>

<tr>
	<td>moderation_do_move</td>
	<td></td>
	<td>904</td>
</tr>

<tr>
	<td>moderation_viewthreadnotes</td>
	<td></td>
	<td>944</td>
</tr>

<tr>
	<td>moderation_threadnotes</td>
	<td></td>
	<td>1104</td>
</tr>

<tr>
	<td>moderation_do_threadnotes</td>
	<td></td>
	<td>1121</td>
</tr>

<tr>
	<td>moderation_getip</td>
	<td></td>
	<td>1156</td>
</tr>

<tr>
	<td>moderation_getpmip</td>
	<td></td>
	<td>1195</td>
</tr>

<tr>
	<td>moderation_merge</td>
	<td></td>
	<td>1209</td>
</tr>

<tr>
	<td>moderation_do_merge</td>
	<td></td>
	<td>1226</td>
</tr>

<tr>
	<td>moderation_split</td>
	<td></td>
	<td>1357</td>
</tr>

<tr>
	<td>moderation_do_split</td>
	<td></td>
	<td>1374</td>
</tr>

<tr>
	<td>moderation_removesubscriptions</td>
	<td></td>
	<td>1436</td>
</tr>

<tr>
	<td>moderation_purgespammer_purge</td>
	<td></td>
	<td>2777</td>
</tr>

<tr>
	<td>moderation_purgespammer_show</td>
	<td></td>
	<td>2864</td>
</tr>

<tr>
	<td>moderation_confirmation</td>
	<td></td>
	<td>2906</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> newreply.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>newreply_do_newreply_start</td>
	<td></td>
	<td>298</td>
</tr>

<tr>
	<td>newreply_do_newreply_end</td>
	<td></td>
	<td>588</td>
</tr>

<tr>
	<td>newreply_start</td>
	<td></td>
	<td>727</td>
</tr>

<tr>
	<td>newreply_end</td>
	<td></td>
	<td>1491</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> newthread.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>newthread_do_newthread_start</td>
	<td></td>
	<td>250</td>
</tr>

<tr>
	<td>newthread_do_newthread_end</td>
	<td></td>
	<td>488</td>
</tr>

<tr>
	<td>newthread_start</td>
	<td></td>
	<td>501</td>
</tr>

<tr>
	<td>newthread_end</td>
	<td></td>
	<td>1129</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> online.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>online_today_start</td>
	<td></td>
	<td>37</td>
</tr>

<tr>
	<td>online_today_end</td>
	<td></td>
	<td>119</td>
</tr>

<tr>
	<td>online_start</td>
	<td></td>
	<td>126</td>
</tr>

<tr>
	<td>online_user</td>
	<td></td>
	<td>220</td>
</tr>

<tr>
	<td>online_end</td>
	<td></td>
	<td>280</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> polls.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>polls_start</td>
	<td></td>
	<td>23</td>
</tr>

<tr>
	<td>polls_newpoll_start</td>
	<td></td>
	<td>51</td>
</tr>

<tr>
	<td>polls_newpoll_end</td>
	<td></td>
	<td>179</td>
</tr>

<tr>
	<td>polls_do_newpoll_start</td>
	<td></td>
	<td>189</td>
</tr>

<tr>
	<td>polls_do_newpoll_process</td>
	<td></td>
	<td>342</td>
</tr>

<tr>
	<td>polls_do_newpoll_end</td>
	<td></td>
	<td>348</td>
</tr>

<tr>
	<td>polls_editpoll_start</td>
	<td></td>
	<td>364</td>
</tr>

<tr>
	<td>polls_editpoll_end</td>
	<td></td>
	<td>556</td>
</tr>

<tr>
	<td>polls_do_editpoll_start</td>
	<td></td>
	<td>567</td>
</tr>

<tr>
	<td>polls_do_editpoll_process</td>
	<td></td>
	<td>735</td>
</tr>

<tr>
	<td>polls_do_editpoll_end</td>
	<td></td>
	<td>739</td>
</tr>

<tr>
	<td>polls_showresults_start</td>
	<td></td>
	<td>776</td>
</tr>

<tr>
	<td>polls_showresults_end</td>
	<td></td>
	<td>902</td>
</tr>

<tr>
	<td>polls_vote_start</td>
	<td></td>
	<td>921</td>
</tr>

<tr>
	<td>polls_vote_process</td>
	<td></td>
	<td>1062</td>
</tr>

<tr>
	<td>polls_vote_end</td>
	<td></td>
	<td>1066</td>
</tr>

<tr>
	<td>polls_do_undovote_start</td>
	<td></td>
	<td>1088</td>
</tr>

<tr>
	<td>polls_do_undovote_process</td>
	<td></td>
	<td>1201</td>
</tr>

<tr>
	<td>polls_do_undovote_end</td>
	<td></td>
	<td>1206</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> portal.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>portal_start</td>
	<td></td>
	<td>58</td>
</tr>

<tr>
	<td>portal_announcement</td>
	<td></td>
	<td>585</td>
</tr>

<tr>
	<td>portal_end</td>
	<td></td>
	<td>701</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> printthread.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>printthread_start</td>
	<td></td>
	<td>24</td>
</tr>

<tr>
	<td>printthread_start</td>
	<td></td>
	<td>33</td>
</tr>

<tr>
	<td>printthread_post</td>
	<td></td>
	<td>185</td>
</tr>

<tr>
	<td>printthread_end</td>
	<td></td>
	<td>189</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> private.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>private_start</td>
	<td></td>
	<td>95</td>
</tr>

<tr>
	<td>private_do_search_start</td>
	<td></td>
	<td>133</td>
</tr>

<tr>
	<td>private_do_search_process</td>
	<td></td>
	<td>214</td>
</tr>

<tr>
	<td>private_do_search_end</td>
	<td></td>
	<td>239</td>
</tr>

<tr>
	<td>private_results_start</td>
	<td></td>
	<td>254</td>
</tr>

<tr>
	<td>private_results_end</td>
	<td></td>
	<td>506</td>
</tr>

<tr>
	<td>private_advanced_search</td>
	<td></td>
	<td>514</td>
</tr>

<tr>
	<td>private_send_do_send</td>
	<td></td>
	<td>561</td>
</tr>

<tr>
	<td>private_do_send_end</td>
	<td></td>
	<td>650</td>
</tr>

<tr>
	<td>private_send_start</td>
	<td></td>
	<td>670</td>
</tr>

<tr>
	<td>private_send_end</td>
	<td></td>
	<td>962</td>
</tr>

<tr>
	<td>private_read</td>
	<td></td>
	<td>970</td>
</tr>

<tr>
	<td>private_read_end</td>
	<td></td>
	<td>1216</td>
</tr>

<tr>
	<td>private_tracking_start</td>
	<td></td>
	<td>1229</td>
</tr>

<tr>
	<td>private_tracking_end</td>
	<td></td>
	<td>1354</td>
</tr>

<tr>
	<td>private_do_tracking_start</td>
	<td></td>
	<td>1365</td>
</tr>

<tr>
	<td>private_do_tracking_end</td>
	<td></td>
	<td>1380</td>
</tr>

<tr>
	<td>private_do_tracking_end</td>
	<td></td>
	<td>1396</td>
</tr>

<tr>
	<td>private_do_tracking_end</td>
	<td></td>
	<td>1423</td>
</tr>

<tr>
	<td>private_stopalltracking_start</td>
	<td></td>
	<td>1433</td>
</tr>

<tr>
	<td>private_stopalltracking_end</td>
	<td></td>
	<td>1440</td>
</tr>

<tr>
	<td>private_folders_start</td>
	<td></td>
	<td>1446</td>
</tr>

<tr>
	<td>private_folders_end</td>
	<td></td>
	<td>1477</td>
</tr>

<tr>
	<td>private_do_folders_start</td>
	<td></td>
	<td>1488</td>
</tr>

<tr>
	<td>private_do_folders_end</td>
	<td></td>
	<td>1581</td>
</tr>

<tr>
	<td>private_empty_start</td>
	<td></td>
	<td>1593</td>
</tr>

<tr>
	<td>private_empty_end</td>
	<td></td>
	<td>1608</td>
</tr>

<tr>
	<td>private_do_empty_start</td>
	<td></td>
	<td>1619</td>
</tr>

<tr>
	<td>private_do_empty_end</td>
	<td></td>
	<td>1652</td>
</tr>

<tr>
	<td>private_do_stuff</td>
	<td></td>
	<td>1661</td>
</tr>

<tr>
	<td>private_delete_start</td>
	<td></td>
	<td>1750</td>
</tr>

<tr>
	<td>private_delete_end</td>
	<td></td>
	<td>1769</td>
</tr>

<tr>
	<td>private_export_start</td>
	<td></td>
	<td>1780</td>
</tr>

<tr>
	<td>private_export_end</td>
	<td></td>
	<td>1797</td>
</tr>

<tr>
	<td>private_do_export_start</td>
	<td></td>
	<td>1809</td>
</tr>

<tr>
	<td>private_do_export_end</td>
	<td></td>
	<td>2035</td>
</tr>

<tr>
	<td>private_inbox</td>
	<td></td>
	<td>2078</td>
</tr>

<tr>
	<td>private_message</td>
	<td></td>
	<td>2393</td>
</tr>

<tr>
	<td>private_end</td>
	<td></td>
	<td>2473</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> ratethread.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>ratethread_start</td>
	<td></td>
	<td>92</td>
</tr>

<tr>
	<td>ratethread_process</td>
	<td></td>
	<td>111</td>
</tr>

<tr>
	<td>ratethread_end</td>
	<td></td>
	<td>140</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> report.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>report_start</td>
	<td></td>
	<td>25</td>
</tr>

<tr>
	<td>report_type</td>
	<td></td>
	<td>130</td>
</tr>

<tr>
	<td>report_do_report_start</td>
	<td></td>
	<td>156</td>
</tr>

<tr>
	<td>report_do_report_end</td>
	<td></td>
	<td>165</td>
</tr>

<tr>
	<td>report_do_report_end</td>
	<td></td>
	<td>205</td>
</tr>

<tr>
	<td>report_end</td>
	<td></td>
	<td>255</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> reputation.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>reputation_start</td>
	<td></td>
	<td>24</td>
</tr>

<tr>
	<td>reputation_do_add_start</td>
	<td></td>
	<td>245</td>
</tr>

<tr>
	<td>reputation_do_add_process</td>
	<td></td>
	<td>384</td>
</tr>

<tr>
	<td>reputation_do_add_end</td>
	<td></td>
	<td>412</td>
</tr>

<tr>
	<td>reputation_add_start</td>
	<td></td>
	<td>422</td>
</tr>

<tr>
	<td>reputation_add_end</td>
	<td></td>
	<td>498</td>
</tr>

<tr>
	<td>reputation_add_end_error</td>
	<td></td>
	<td>505</td>
</tr>

<tr>
	<td>reputation_vote</td>
	<td></td>
	<td>1052</td>
</tr>

<tr>
	<td>reputation_end</td>
	<td></td>
	<td>1063</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> search.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>search_results_start</td>
	<td></td>
	<td>67</td>
</tr>

<tr>
	<td>search_results_thread</td>
	<td></td>
	<td>631</td>
</tr>

<tr>
	<td>search_results_end</td>
	<td></td>
	<td>676</td>
</tr>

<tr>
	<td>search_results_post</td>
	<td></td>
	<td>1025</td>
</tr>

<tr>
	<td>search_results_end</td>
	<td></td>
	<td>1071</td>
</tr>

<tr>
	<td>search_do_search_process</td>
	<td></td>
	<td>1150</td>
</tr>

<tr>
	<td>search_do_search_process</td>
	<td></td>
	<td>1227</td>
</tr>

<tr>
	<td>search_do_search_process</td>
	<td></td>
	<td>1275</td>
</tr>

<tr>
	<td>search_do_search_process</td>
	<td></td>
	<td>1343</td>
</tr>

<tr>
	<td>search_do_search_process</td>
	<td></td>
	<td>1420</td>
</tr>

<tr>
	<td>search_do_search_start</td>
	<td></td>
	<td>1426</td>
</tr>

<tr>
	<td>search_do_search_process</td>
	<td></td>
	<td>1512</td>
</tr>

<tr>
	<td>search_do_search_end</td>
	<td></td>
	<td>1525</td>
</tr>

<tr>
	<td>search_thread_start</td>
	<td></td>
	<td>1563</td>
</tr>

<tr>
	<td>search_thread_process</td>
	<td></td>
	<td>1631</td>
</tr>

<tr>
	<td>search_do_search_end</td>
	<td></td>
	<td>1635</td>
</tr>

<tr>
	<td>search_start</td>
	<td></td>
	<td>1640</td>
</tr>

<tr>
	<td>search_end</td>
	<td></td>
	<td>1653</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> sendthread.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>sendthread_do_sendtofriend_start</td>
	<td></td>
	<td>150</td>
</tr>

<tr>
	<td>sendthread_do_sendtofriend_end</td>
	<td></td>
	<td>235</td>
</tr>

<tr>
	<td>sendthread_start</td>
	<td></td>
	<td>246</td>
</tr>

<tr>
	<td>sendthread_end</td>
	<td></td>
	<td>290</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> showteam.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>showteam_start</td>
	<td></td>
	<td>22</td>
</tr>

<tr>
	<td>showteam_user</td>
	<td></td>
	<td>175</td>
</tr>

<tr>
	<td>showteam_end</td>
	<td></td>
	<td>205</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> showthread.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>showthread_start</td>
	<td></td>
	<td>430</td>
</tr>

<tr>
	<td>showthread_poll_results</td>
	<td></td>
	<td>589</td>
</tr>

<tr>
	<td>showthread_poll</td>
	<td></td>
	<td>606</td>
</tr>

<tr>
	<td>showthread_ismod</td>
	<td></td>
	<td>676</td>
</tr>

<tr>
	<td>showthread_threaded</td>
	<td></td>
	<td>875</td>
</tr>

<tr>
	<td>showthread_linear</td>
	<td></td>
	<td>1066</td>
</tr>

<tr>
	<td>showthread_end</td>
	<td></td>
	<td>1522</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> stats.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>stats_start</td>
	<td></td>
	<td>37</td>
</tr>

<tr>
	<td>stats_end</td>
	<td></td>
	<td>203</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> syndication.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>syndication_start</td>
	<td></td>
	<td>69</td>
</tr>

<tr>
	<td>syndication_get_posts</td>
	<td></td>
	<td>173</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> usercp.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>usercp_start</td>
	<td></td>
	<td>57</td>
</tr>

<tr>
	<td>usercp_do_profile_start</td>
	<td></td>
	<td>188</td>
</tr>

<tr>
	<td>usercp_do_profile_end</td>
	<td></td>
	<td>318</td>
</tr>

<tr>
	<td>usercp_profile_start</td>
	<td></td>
	<td>347</td>
</tr>

<tr>
	<td>usercp_profile_end</td>
	<td></td>
	<td>772</td>
</tr>

<tr>
	<td>usercp_do_options_start</td>
	<td></td>
	<td>783</td>
</tr>

<tr>
	<td>usercp_do_options_end</td>
	<td></td>
	<td>848</td>
</tr>

<tr>
	<td>usercp_options_start</td>
	<td></td>
	<td>856</td>
</tr>

<tr>
	<td>usercp_options_end</td>
	<td></td>
	<td>1189</td>
</tr>

<tr>
	<td>usercp_do_email_start</td>
	<td></td>
	<td>1202</td>
</tr>

<tr>
	<td>usercp_do_email_verify</td>
	<td></td>
	<td>1251</td>
</tr>

<tr>
	<td>usercp_do_email_changed</td>
	<td></td>
	<td>1260</td>
</tr>

<tr>
	<td>usercp_email</td>
	<td></td>
	<td>1285</td>
</tr>

<tr>
	<td>usercp_do_password_start</td>
	<td></td>
	<td>1298</td>
</tr>

<tr>
	<td>usercp_do_password_end</td>
	<td></td>
	<td>1331</td>
</tr>

<tr>
	<td>usercp_password</td>
	<td></td>
	<td>1344</td>
</tr>

<tr>
	<td>usercp_do_changename_start</td>
	<td></td>
	<td>1355</td>
</tr>

<tr>
	<td>usercp_do_changename_end</td>
	<td></td>
	<td>1385</td>
</tr>

<tr>
	<td>usercp_changename_start</td>
	<td></td>
	<td>1399</td>
</tr>

<tr>
	<td>usercp_changename_end</td>
	<td></td>
	<td>1405</td>
</tr>

<tr>
	<td>usercp_do_subscriptions_start</td>
	<td></td>
	<td>1416</td>
</tr>

<tr>
	<td>usercp_subscriptions_start</td>
	<td></td>
	<td>1459</td>
</tr>

<tr>
	<td>usercp_subscriptions_end</td>
	<td></td>
	<td>1787</td>
</tr>

<tr>
	<td>usercp_forumsubscriptions_start</td>
	<td></td>
	<td>1795</td>
</tr>

<tr>
	<td>usercp_forumsubscriptions_end</td>
	<td></td>
	<td>1912</td>
</tr>

<tr>
	<td>usercp_do_editsig_start</td>
	<td></td>
	<td>1923</td>
</tr>

<tr>
	<td>usercp_do_editsig_process</td>
	<td></td>
	<td>1948</td>
</tr>

<tr>
	<td>usercp_do_editsig_end</td>
	<td></td>
	<td>1950</td>
</tr>

<tr>
	<td>usercp_editsig_start</td>
	<td></td>
	<td>1956</td>
</tr>

<tr>
	<td>usercp_editsig_end</td>
	<td></td>
	<td>2019</td>
</tr>

<tr>
	<td>usercp_editsig_end</td>
	<td></td>
	<td>2068</td>
</tr>

<tr>
	<td>usercp_do_avatar_start</td>
	<td></td>
	<td>2081</td>
</tr>

<tr>
	<td>usercp_do_avatar_end</td>
	<td></td>
	<td>2225</td>
</tr>

<tr>
	<td>usercp_avatar_start</td>
	<td></td>
	<td>2237</td>
</tr>

<tr>
	<td>usercp_avatar_end</td>
	<td></td>
	<td>2288</td>
</tr>

<tr>
	<td>usercp_acceptrequest_start</td>
	<td></td>
	<td>2312</td>
</tr>

<tr>
	<td>usercp_acceptrequest_end</td>
	<td></td>
	<td>2399</td>
</tr>

<tr>
	<td>usercp_declinerequest_start</td>
	<td></td>
	<td>2416</td>
</tr>

<tr>
	<td>usercp_declinerequest_end</td>
	<td></td>
	<td>2428</td>
</tr>

<tr>
	<td>usercp_cancelrequest_start</td>
	<td></td>
	<td>2445</td>
</tr>

<tr>
	<td>usercp_cancelrequest_end</td>
	<td></td>
	<td>2449</td>
</tr>

<tr>
	<td>usercp_do_editlists_start</td>
	<td></td>
	<td>2459</td>
</tr>

<tr>
	<td>usercp_do_editlists_end</td>
	<td></td>
	<td>2783</td>
</tr>

<tr>
	<td>usercp_editlists_start</td>
	<td></td>
	<td>2845</td>
</tr>

<tr>
	<td>usercp_editlists_end</td>
	<td></td>
	<td>2997</td>
</tr>

<tr>
	<td>usercp_drafts_start</td>
	<td></td>
	<td>3005</td>
</tr>

<tr>
	<td>usercp_drafts_end</td>
	<td></td>
	<td>3059</td>
</tr>

<tr>
	<td>usercp_do_drafts_start</td>
	<td></td>
	<td>3070</td>
</tr>

<tr>
	<td>usercp_do_drafts_end</td>
	<td></td>
	<td>3109</td>
</tr>

<tr>
	<td>usercp_usergroups_start</td>
	<td></td>
	<td>3115</td>
</tr>

<tr>
	<td>usercp_usergroups_change_displaygroup</td>
	<td></td>
	<td>3138</td>
</tr>

<tr>
	<td>usercp_usergroups_leave_group</td>
	<td></td>
	<td>3164</td>
</tr>

<tr>
	<td>usercp_usergroups_join_group_request</td>
	<td></td>
	<td>3239</td>
</tr>

<tr>
	<td>usercp_usergroups_join_group</td>
	<td></td>
	<td>3253</td>
</tr>

<tr>
	<td>usercp_usergroups_accept_invite</td>
	<td></td>
	<td>3277</td>
</tr>

<tr>
	<td>usercp_usergroups_end</td>
	<td></td>
	<td>3493</td>
</tr>

<tr>
	<td>usercp_attachments_start</td>
	<td></td>
	<td>3501</td>
</tr>

<tr>
	<td>usercp_attachments_end</td>
	<td></td>
	<td>3600</td>
</tr>

<tr>
	<td>usercp_do_attachments_start</td>
	<td></td>
	<td>3611</td>
</tr>

<tr>
	<td>usercp_do_attachments_end</td>
	<td></td>
	<td>3623</td>
</tr>

<tr>
	<td>usercp_do_notepad_start</td>
	<td></td>
	<td>3638</td>
</tr>

<tr>
	<td>usercp_do_notepad_end</td>
	<td></td>
	<td>3640</td>
</tr>

<tr>
	<td>usercp_notepad_start</td>
	<td></td>
	<td>3801</td>
</tr>

<tr>
	<td>usercp_notepad_end</td>
	<td></td>
	<td>3804</td>
</tr>

<tr>
	<td>usercp_end</td>
	<td></td>
	<td>4202</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> usercp2.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>usercp2_start</td>
	<td></td>
	<td>34</td>
</tr>

<tr>
	<td>usercp2_do_addsubscription</td>
	<td></td>
	<td>66</td>
</tr>

<tr>
	<td>usercp2_addsubscription_forum</td>
	<td></td>
	<td>95</td>
</tr>

<tr>
	<td>usercp2_addsubscription_thread</td>
	<td></td>
	<td>166</td>
</tr>

<tr>
	<td>usercp2_removesubscription_forum</td>
	<td></td>
	<td>183</td>
</tr>

<tr>
	<td>usercp2_removesubscription_thread</td>
	<td></td>
	<td>220</td>
</tr>

<tr>
	<td>usercp2_removesubscriptions_forum</td>
	<td></td>
	<td>238</td>
</tr>

<tr>
	<td>usercp2_removesubscriptions_thread</td>
	<td></td>
	<td>253</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> warnings.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>warnings_start</td>
	<td></td>
	<td>39</td>
</tr>

<tr>
	<td>warnings_do_warn_start</td>
	<td></td>
	<td>71</td>
</tr>

<tr>
	<td>warnings_do_warn_end</td>
	<td></td>
	<td>127</td>
</tr>

<tr>
	<td>warnings_warning</td>
	<td></td>
	<td>291</td>
</tr>

<tr>
	<td>warnings_warn_start</td>
	<td></td>
	<td>300</td>
</tr>

<tr>
	<td>warnings_warn_end</td>
	<td></td>
	<td>491</td>
</tr>

<tr>
	<td>warnings_do_revoke_start</td>
	<td></td>
	<td>528</td>
</tr>

<tr>
	<td>warnings_view_start</td>
	<td></td>
	<td>589</td>
</tr>

<tr>
	<td>warnings_view_end</td>
	<td></td>
	<td>686</td>
</tr>

<tr>
	<td>warnings_warning</td>
	<td></td>
	<td>844</td>
</tr>

<tr>
	<td>warnings_end</td>
	<td></td>
	<td>853</td>
</tr>


<tr class="file">
<td colspan="3" class="tcat"><strong>File: </strong> xmlhttp.php</td>
</tr>
<tr class="heading">
<td>Hook</td>
<td>Params</td>
<td>Line</td>
</tr>

<tr>
	<td>xmlhttp</td>
	<td></td>
	<td>205</td>
</tr>

<tr>
	<td>xmlhttp_get_users_start</td>
	<td></td>
	<td>252</td>
</tr>

<tr>
	<td>xmlhttp_get_users_end</td>
	<td></td>
	<td>271</td>
</tr>

<tr>
	<td>xmlhttp_edit_subject_start</td>
	<td></td>
	<td>320</td>
</tr>

<tr>
	<td>xmlhttp_edit_subject_end</td>
	<td></td>
	<td>408</td>
</tr>

<tr>
	<td>xmlhttp_edit_post_start</td>
	<td></td>
	<td>451</td>
</tr>

<tr>
	<td>xmlhttp_edit_post_end</td>
	<td></td>
	<td>479</td>
</tr>

<tr>
	<td>xmlhttp_update_post</td>
	<td></td>
	<td>638</td>
</tr>

<tr>
	<td>xmlhttp_get_multiquoted_start</td>
	<td></td>
	<td>655</td>
</tr>

<tr>
	<td>xmlhttp_get_multiquoted_intermediate</td>
	<td></td>
	<td>700</td>
</tr>

<tr>
	<td>xmlhttp_get_multiquoted_end</td>
	<td></td>
	<td>728</td>
</tr>

<tr>
	<td>xmlhttp_refresh_captcha</td>
	<td></td>
	<td>750</td>
</tr>

<tr>
	<td>xmlhttp_validate_captcha</td>
	<td></td>
	<td>769</td>
</tr>

<tr>
	<td>xmlhttp_refresh_question</td>
	<td></td>
	<td>815</td>
</tr>

<tr>
	<td>xmlhttp_validate_question</td>
	<td></td>
	<td>861</td>
</tr>

<tr>
	<td>xmlhttp_complex_password</td>
	<td></td>
	<td>884</td>
</tr>

<tr>
	<td>xmlhttp_username_availability</td>
	<td></td>
	<td>941</td>
</tr>

<tr>
	<td>xmlhttp_username_exists</td>
	<td></td>
	<td>977</td>
</tr>

<tr>
	<td>xmlhttp_get_buddyselect_start</td>
	<td></td>
	<td>1004</td>
</tr>

<tr>
	<td>xmlhttp_get_buddyselect_end</td>
	<td></td>
	<td>1026</td>
</tr>
		
	
</tbody>
</table>
