# What To Include In functions.php File

## Description

In this lesson you will learn that WordPress themes often include a file named functions.php, which is where unique features and custom functions can be added. However, plugins are also meant to add features and functionalities to your site. When should you use functions.php to add your custom code and when should you use plugins?  This lesson will help you understand the difference between the two.

## Objectives

After completing this lesson, you will be able to:

*   Recognize and identify the uses of functions.php in comparison to using plugins to add functionality.
*   Explain when and when not to use functions.php.

## Prerequisite Skills

You will be better equipped to work through this lesson if you have:

*   Basic knowledge of how to write a [theme](https://codex.wordpress.org/Theme_Development) and a [plugin](https://codex.wordpress.org/Writing_a_Plugin)
*   Basic familiarity with PHP and WordPress code

## Assets

*   WordPress installed locally
*   Two or more installed WordPress themes

## Screening Questions

*   Are you familiar with installing and activating themes via the WordPress Dashboard?
*   Will you have a locally or remotely hosted sandbox WordPress site to use during class?
*   Do you feel comfortable using a text editor to edit code?
*   Have you ever added custom functionality to your WordPress site?
*   Are you familiar with the file hierarchy of WordPress themes?

## Teacher Notes

*   It is easiest for students to work on a locally installed copy of WordPress. Set some time aside before class to assist students with installing WordPress locally if they need it. For more information on how to install WordPress locally, please visit [Installing on a Local Server](https://make.wordpress.org/core/handbook/installing-a-local-server/ "Installing on a Local Server").
*   The preferred answers to the screening questions is “yes.” Participants who reply “no” to all questions may not be ready for this lesson.

## Hands-on Walkthrough

### Introduction: What is a functions.php file?

The functions.php file is used to add, remove, or otherwise change the default behaviors of WordPress. The file resides inside the theme's folder. functions.php behaves like a [WordPress Plugin](https://codex.wordpress.org/Plugins "Plugins"), allowing the author to add custom features and functionality to a WordPress site. A child theme can have its own functions.php. However unlike style.css, the functions.php of a child theme does not override the parent theme's functions.php. Instead, it is loaded in addition to the parent’s functions.php. ([read more here](https://codex.wordpress.org/Child_Themes#Using_functions.php))

### How is functions.php different from a plugin?

Since functions.php and plugins both allow you to create custom functionality and modify default behaviour in WordPress, it can be a bit confusing to understand when to use functions.php and when to create or use a plugin to add functionality, but by looking into both methods in more detail you can get a better understanding of when each solution is appropriate. In general, plugins are independent modules that can be downloaded and installed on your WordPress website. The purpose of a plugin is to extend WordPress' functionality or add new features. No modification of the active theme is required to activate plugins. In contrast, themes are a group of files designed to modify the way WordPress looks. While themes can include custom functionality (custom post types, a visual configuration panel, etc), for the most part you select themes based on the way they'll modify how the user experiences your website. The basic characteristics that define and distinguish WordPress plugins versus the functions.php file are: **A WordPress plugin...**

*   requires specific, unique header text.
*   is stored in <tt>wp-content/plugins</tt>, usually in a subdirectory.
*   executes only when individually activated, via the "plugins" panel.
*   applies to all themes.
*   should have a single purpose, e.g., convert posts to pages, offer search engine optimization features, or help with backups.

**A functions.php file...**

*   requires no unique header text.
*   is stored with each Theme in the Theme's subdirectory in <tt>wp-content/themes</tt>.
*   executes only when in the currently activated theme's directory.
*   applies only to that theme. If the Theme is changed, the functionality is lost.
*   can have numerous blocks of code used for many different purposes.

### When to use functions.php

We could infer that if the custom functionality relates to visual presentation, it should reside in functions.php, and if it relates to how the site behaves, it should be stored in a plugin. However, it is technically possible to store visual presentation customizations in a plugin, so how do we determine which is best? The answer is surprisingly simple. The question we need to ask ourselves is: should this functionality be tied to one specific theme or not? Since functions.php resides in a theme folder, that theme must be active for any custom functionality to work. However, if such custom functionality were stored in a plugin, you could switch themes and still retain the custom functionality. Thus the best way to determine how to include your custom code is whether the functionality is specific to a theme or whether the functionality supports the content or structure of the site regardless of what theme is enabled. For instance, you may want to have a unique excerpt length for posts on a specific theme based on its design and layout, therefore excerpt functionality should be added to functions.php. If you want to implement a "read more" link for all posts regardless of which theme you use, this function should be added as a plugin.

### Things that could go into functions.php:

*   content formatting
*   theme specific header and footer functionalities
*   WordPress hooks to change output, for example using the excerpt_length filter to change the length of a post excerpt
*   code that enables theme support for post thumbnails, post formats, and navigation menus
*   functions you'd like to reuse in multiple theme template files

### Things that shouldn't go into functions.php:

*   SEO related functionalities
*   Google Analytics scripts
*   Custom post types and taxonomies

## Exercises

**Add functionality only to functions.php.**

1.  Add custom excerpt length functionality to your active theme's functions.php file by inserting the following code into the file: `<?php function themename_custom_excerpt_length( $length ) { return 40; //number of words in excerpt } add_filter( 'excerpt_length', 'themename_custom_excerpt_length'); ?>`
2.  Create a test blog post with a long excerpt. Verify it works correctly, then switch themes.
3.  Notice that the functionality no longer exists because it was placed in a specific theme's functions.php file.

## Quiz

**Which of the following should not be in function.php?**

1.  Sidebar styling
2.  Favicon
3.  Custom background

**Answer**: 2\. Favicon

## Additional Resources

[Function files explained](https://codex.wordpress.org/Functions_File_Explained) @ Codex
