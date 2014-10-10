# CodeIgniter - minify

## Overview

Simple CodeIgniter library to compress **CSS and JavaScript** files on the fly.

Library is based on few other scripts like <http://code.google.com/p/minify/> 
or <https://code.google.com/p/cssmin> to minify CSS and it uses
[Google Closure compiler](https://developers.google.com/closure/compiler/) to 
compress JavaScript

###INSTALATION:
Just put Minify.php file in libraries path, and create config file on config directory.

###USING THE LIBRARY:

####Configure the library:
All directories needs to be writeable.

	// output path where the compiled files will be stored
    $config['assets_dir'] = 'assets/'; 	
    
    // where to look for css files 
    $config['css_dir'] = 'assets/css';
    
    // where to look for js files 
	$config['js_dir'] = 'assets/js'; 

	// compression engine setting
	$config['compression_engine'] = array('css' => 'minify', 'js' => 'closurecompiler'); // cssmin


####Run the library
In the controller

    //load the library
	$this->load->library('minify'); 

In view	

	// add css files
	$this->minify->css(array('reset.css', 'style.css', 'tinybox.css')); 
	
	// add js files
	$this->minify->js(array('html5.js', 'main.js')); 
	
	// bool argument for rebuild css (false means skip rebuilding). 
	echo $this->minify->deploy_css();

    //Output: '<link href="path-to-compiled-css" rel="stylesheet" type="text/css" />'
    
    // bool argument for rebuild js (false means skip rebuilding). 
    echo $this->minify->deploy_js(); 
 
    //Outputs '<script type="text/javascript" src="path-to-compiled-js"></script>'.
    
### Changelog

14 July
* small bug fixes in JS compression


4 July 2014
* sample JavaScript files to see how it works 
* detection of empty JS file couses force refresh

23 May 2014

* you can chose your compression engine library in config file (CSS only)
* speed optimisations
* force CSS rewrite using $this->minify->deploy_css(TRUE);

11 Mar 2014

* completly rewrite CSS parser - uses cssmin compress CSS,
* detects file modification time no longer force rewrites,
* example usage now included withing app

### Any questions ?

Report theme here: <https://github.com/slav123/CodeIgniter-minify/issues>

### Sponsors

![PHP Storm](http://www.jetbrains.com/img/banners/ps7.png)

