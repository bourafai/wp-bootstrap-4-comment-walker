# wp-bootstrap-4-comment-walker
A custom WordPress comment walker class, to implement the [Bootstrap 4 (Alpha) Media object](https://v4-alpha.getbootstrap.com/layout/media-object/) in wordpress comments list.

for Demo with some css here on [codepen](http://codepen.io/bourafai/pen/QpzyjZ)

Installation and Usage
------------
If you haven't already add the HTML5 theme support for comment list, add this first in your `functions.php`

```php
function custom_theme_setup() {
    add_theme_support( 'html5', array( 'comment-list' ) );
}
add_action( 'after_setup_theme', 'custom_theme_setup' );
```

Place **class-wp-bootstrap-comment-walker.php** in your WordPress theme folder `/wp-content/your-theme/`

Open your WordPress themes **comments.php** file  `/wp-content/your-theme/comments.php` and add this snippet if of code if you don't find it.

```php
<ol class="medias py-md-5 my-md-5 px-sm-0 mx-sm-0">
<?php 
  require_once('class-wp-bootstrap-comment-walker.php');

  wp_list_comments( array(
      'style'         => 'ol',
      'max_depth'     => 4,
      'short_ping'    => true,
      'avatar_size'   => '50',
      'walker'        => new Bootstrap_Comment_Walker(),
  ) );
?>
</ol>
