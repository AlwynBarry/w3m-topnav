# w3m-topnav
Multi-level Navigation Menu using w3.css which properly collapses for mobile devices

# Technologies
Uses w3.css (see https://www.w3schools.com/w3css/)

# Installation
Copy the directories `js` and `styles` to the base of your website

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

2. In your webpage where the menu appears use a `nav` to contain the menu as follows:

```
<nav class="w3-bar-item w3m w3-right">
</nav>
```
(You can remove the w3-right - it simply pulls the menu to the right hand side to make way for icons or site titles to the left)
All code below is within this `nav`

3. Create the menu bar:

```
<div class="w3-bar w3-padding-24">
</div>
```

All code below is added within this `div`

4. In this `div` add a 'close' button (only displayed when the menu is on a mobile screen)

```
<button class="w3-bar-item w3-button w3m-control w3m-close-button" onclick="w3m_closeSideMenu()">Close</button>
```

5. Add top-level and sub-menu items following this pattern:

```
<div class="w3-dropdown-hover w3m-pull-left">  <!-- Start of first menu item -->
  <!-- w3m-pull-left causes any submenus to be pulled left if you want that. -->

  <!-- Provide the top bar menu dropdown label -->
  <div class ="w3m-caret-container">
    <a class="w3-button" href="#">Menu Label<i class="w3m-caret fa fa-angle-down"></i></a>
    <button onclick="w3m_caretClick(this)" class="w3m-clickable-caret fa fa-angle-right"></button>
  </div>

  <!-- Now provide the submenu items which will be in the dropdown -->
  <div class="w3-dropdown-content w3-bar-block w3-card-4">
    <!-- These are normal submenu links without further submenus -->
    <a class="w3-bar-item w3-button" href="#">Link 1</a>
    <a class="w3-bar-item w3-button" href="#">Link 2</a>
    <a class="w3-bar-item w3-button" href="#">Link 3</a>

    <!-- This is an example of a link to a lower submenu which is pulled right or left -->
    <div class="w3-dropdown-hover">
      <!-- This is the submenu button -->
      <div class ="w3m-caret-container">
        <a class="w3-button" href="2">Dropdown 2.1  <i class="w3m-caret fa fa-angle-right"></i></a>
			<button onclick="w3m_caretClick(this)" class="w3m-clickable-caret fa fa-angle-right"></button>
      </div>
      <!-- This is the pull left/right submenu -->
      <div class="w3-dropdown-content w3-bar-block w3-card-4">
        <a class="w3-bar-item w3-button">link 1</a>
        <a class="w3-bar-item w3-button">link 2</a>
      </div><!-- w3-dropdown-content -->
    </div><!-- w3-dropdown-hover -->
    <!-- End of dropdown submenu -->
	
    <!-- Other submenu items will follow the same pattern -->

  </div><!-- w3-dropdown-content --> <!-- End of dropdown menu -->
  
</div><!-- w3-dropdpwn-hover --> <!-- End of first menu item -->
```

