# w3m-topnav
Multi-level page top Navigation Menu using w3.css which properly collapses into a pull-left or pull-right menu for mobile devices.
It utilises only w3.css with minimal additional css or Javascript.

Also includes a WordPress `nav-walker.php` sub-class so that Wordpress menus are automatically translated into a html form usable with w3m-topnav on WordPress.

# Author
Alwyn Barry

## Written
Version 0.1: 9/4/2021

## Version
1.0

## Date Published
2022-03-12

# Technologies
Uses w3.css (see https://www.w3schools.com/w3css/)

# Installation
For hard-coded websites:
	Copy the directories `js` and `styles` to the base of your website.
	Follow the Usage instructions below

For Wordpress:
	Copy the directories `inc`, `js` and `styles` to your Theme directory under wp-content/themes.
	Use the following in your theme's `functions.php` to enqueue the style sheet and load the nav-walker class:

```
/**
 * Enqueue scripts and styles.
 */
function wt_scripts() {
	/* NOTE: For the following command you need to download a copy of w3.css from w3schools.com into Theme's your css folder */
	wp_enqueue_style( 'w3css-style', get_template_directory_uri() . '/css/w3.css' );
	/* Now enqueue the css for the w3 enabled navbar */
	wp_enqueue_style( 'w3m-topnav-style', get_template_directory_uri() . '/css/w3m-topnav.css' );
	/* Finally, enqueue the JavaScript for the navbar */
	wp_enqueue_script( 'w3m-topnav-script', get_template_directory_uri() . '/js/w3m-topnav.js', array(), _S_VERSION, true );	
}
add_action( 'wp_enqueue_scripts', 'wt_scripts' );

/**
 * Register Custom Navigation Walker
 */
function register_w3m_navwalker(){
	require_once get_template_directory() . '/inc/class-w3m-nav-walker.php';
}
add_action( 'after_setup_theme', 'register_w3m_navwalker' );
```

# Usage
Look in the file `w3m-topnav-test.html` to see how to use.

Minimally:
1. Add to `<head>` ... `</head>` the following:

```
<link rel="stylesheet" href="https://www.w3schools.com/w3css/4/w3.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
<link rel="stylesheet" href="./styles/w3m-topnav.css">
	
<script type="text/javascript" src="./js/w3m-topnav.js"></script>
```

2. Structure your Webpage header as follows:

```
<!-- The page header which contains your navbar (alongside site icons / titles / etc) -->
<header class="w3m w3-bar">
  <!-- Other header items (site icons / titles / etc) can be added as needed, each one as a w3-bar-item -->
  
  <!-- Add an open button, only shown when on mobile screens to open the menu on demand -->
  <button class="w3-bar-item w3-button w3m-control w3m-open-button" onclick="openSideMenu()">OPEN</button>
  <!-- The nav is your main nav bar in the header -->
  <nav class="w3-bar-item w3m">
    <div class="w3-bar w3-padding-24">
      <!-- Add a close button that is only shown in the mobile menu because the menu is only shown on demand -->
      <button class="w3-bar-item w3-button w3m-control w3m-close-button" onclick="closeSideMenu()">Close</button>
      
      <!-- A top-level menu item without a submenu -->
      <a class="w3-bar-item w3-button">link 1</a>

      <!-- Start of top-level menu item which has a submenu -->
      <div class="w3-dropdown-hover">  <!-- Add w3m-pull-left to cause all submenus to be pulled left if you want that. -->
        <!-- The dropdown button part -->
        <div class="w3m-caret-container">
          <!-- The button text, which contains the caret used in the horizontal pull-right menu --> 
          <a class="w3-button">Dropdown Name <i class="w3m-caret fa fa-angle-right"></i></a>
          <!-- The caret used in the horizontal mobile menu - to be clickable it has to be separate from the button -->
          <button onclick="caretClick(this)" class="w3m-clickable-caret fa fa-angle-right"></button>
        </div>
        <!-- The dropdown submenu content part -->
        <div class="w3-dropdown-content w3-bar-block w3-card-4">
          <a class="w3-bar-item w3-button">link 1</a>
          <a class="w3-bar-item w3-button">link 2</a>
          <!-- ... additional links, including any level 2 pull-left or pull-right dropdowns done in the same way as this drop-down ... -->
        </div> <!-- w3-dropdown-content -->
      </div> <!-- w3-dropdown-hover -->

      <!-- ... additional links, including additional dropdowns ... -->
    </div> <!-- w3-bar -->
  </nav> <!-- w3m -->

  <!-- Other header items can be added as needed -->
</header> <!-- w3-bar -->
```
