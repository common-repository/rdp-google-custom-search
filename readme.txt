=== RDP Google Custom Search ===
Contributors: rpayne7264
Tags: google search, google custom search,google custom search engine, search results, multiple site search
Requires at least: 3.4
Tested up to: 4.6.1
Stable tag: 1.0.0

RDP Google Custom Search lets you use Google's Custom Search Engine (CSE) API to add targeted search capability to your site.

== Description ==
**ATTN: This plugin only works with the PAID version of Google Custom Search.**

With RDP Google Custom Search, you can target your site's contents, or other site's contents. You can add multiple CSEs and allow your visitor to choose one.

RDP Google Custom Search uses a simple shortcode so that a search box can be placed anywhere.

You can put a multi-CSE search box in the main content of your page, and then put another search box in the sidebar that is dedicated to only one CSE, such as your site.

Each search box also provides a **Page** selector, which will search the current page and highlight matching text.

The results are displayed using a special template that replaces the content of the current page/post and that can be styled as desired. The default width of the results content is 980px. The built-in rendering function marks up the results to use Google styling HTML and class names.

This plugin can be used with the RDP Wiki Embed plugin, which allows you to have the links in the search results that point to MediaWiki sites to postback and display content on your own web site.


== Frequently Asked Questions ==


== Usage ==

RDP Google Custom Search is implemented using the shortcode [rdp-gcs]. It accepts the following arguments:

* id: (required) comma separated list of id numbers, indicating the CSEs to use
* default: when more than one CSE is selected, this indicates the CSE to use by default

Examples:

[rdp-gcs id='3']

[rdp-gcs id='1,3' default='1']


== Installation ==

1. Upload `rdp-google-custom-search` folder to the `/wp-content/plugins/` directory
2. Activate the plugin through the 'Plugins' menu in WordPress
3. Go to 'RDP GCS' -> 'Add New Google CSE'
4. Fill in the form with a Name, a Menu Title, and the JSON URL to the Google CSE
5. Click the 'Save Changes' button
6. Continue to add any other Google CSEs, by following steps 4 & 5 above

= Extra =
To make everything pretty, add a rdp-gcs.custom.css file to your theme's folder. Start with the rdp-gcs.custom-sample.css file located in the 'pl/style/' folder.


== Screenshots ==

1. A multi-CSE search box in the main content area, and another single-CSE search box in the sidebar
2. CSE picklist attached to a multi-CSE search box
3. Default rendering of search results
4. List of Custom Search Engines added to the plugin.
5. Button to launch shortcode helper form
6. Shortcode helper form
7. Plugin active in the admin menu


== Changelog ==

= 0.1.4 =
* REFACTOR: modified Position Calculator script
* REFACTOR: changed add_object_page to add_menu_page

= 0.1.3 =
* REFACTOR: removed unused admin-side script file reference

= 0.1.2 =
* REFACTOR: fixed downward pointing triangle changing to entity values after picklist switch
* REFACTOR: fixed code to handle search terms containing quotation marks and apostrophes, after postback

= 0.1.1 =
* REFACTOR: added downward pointing triangle to CSE search scope button 

= 0.1.0 = 
* Initial RC


== Upgrade Notice ==


== Other Notes ==

== External Scripts Included ==
* jQuery.PositionCalculator v1.1.2 under MIT License
* jQuery Highlight under MIT License

== PHP Hook Reference: ==

= rdp_gcs_render_search_results_applied =
* Params: none
* Fires after the default render function is added to the filters array. 

= rdp_gcs_styles_enqueued =
* Params: none
* Fires after plugin-specific styles are enqueued

= rdp_gcs_scripts_enqueued =
* Params: none
* Fires after plugin-specific scripts are enqueued


== PHP Filter Reference: ==

= rdp_gcs_before_search_box =
* Param: empty string
* Fires before the rendering of the search box within the results template
* Return: any text/HTML/script to be rendered before the search box

= rdp_gcs_after_search_box =
* Param: empty string
* Fires after the rendering of the search box within the results template
* Return: any text/HTML/script to be rendered after the search box

= rdp_gcs_before_search_results =
* Param: empty string
* Fires before the rendering of the search results within the results template
* Return: any text/HTML/script to be rendered before the search results

= rdp_gcs_render_search_results =
* Param 1: JSON object containing Google API search results or NULL if an error occurred during the API call
* Param 2: string containing the last error message set during the search request or empty string if no error occurred
* This filter is required for hooking into a function that will render the search results. For a custom rendering function, be sure to remove this filter during the rdp_gcs_render_search_results_applied hook, and then re-set this filter to use your custom rendering function

= rdp_gcs_after_search_results =
* Param: empty string
* Fires after the rendering of the search results within the results template
* Return: any text/HTML/script to be rendered after the search results