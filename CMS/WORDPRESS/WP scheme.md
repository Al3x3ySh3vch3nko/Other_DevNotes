___1. ������������� WP

___2. ������� ���� ������

___3. ��������� � ������� PHP
�� ��������� �� ������������ root, ��� ������

___4. � ������� - ������� ��, ���� �������� (��� ������ ����� �� ����������, ��������� �.�. utf8_general_ci),

___5. � ����������� - ������� ������������ (�������� ������� ������),
��� - admin � ������. ������� ����� (���).

___6. � WP - �������� ��� ��, 

___7. ����� ��������� ��� ����� � ��. 

___8. ������� ���� CSS � ��� ��������� �������������� ��������� ���-�� ����:

/*
Theme Name: Twenty Seventeen
Theme URI: https://wordpress.org/themes/twentyseventeen/
Author: the WordPress team
Author URI: https://wordpress.org/
Description: Twenty Seventeen brings your site to life with header video and immersive featured images. 
With a focus on business sites, it features multiple sections on the front page as well as widgets, 
navigation and social menus, a logo, and more. 
Personalize its asymmetrical grid with a custom color scheme and showcase your multimedia content with post formats. 
Our default theme for 2017 works great in many languages, for any abilities, and on any device.
Version: 2.2
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: twentyseventeen
Tags: one-column, two-columns, right-sidebar, flexible-header,
accessibility-ready, custom-colors, custom-header, custom-menu, custom-logo, editor-style,
featured-images, footer-widgets, post-formats, rtl-language-support, sticky-post, theme-options, 
threaded-comments, translation-ready

This theme, like WordPress, is licensed under the GPL.
Use it to make something cool, have fun, and share what you've learned with others.
*/

___9. ������� ���� index.php

___10. ��������� ������ � ����� ��� ������ screenshot.png

___11. ������� ���� 404.php � �������� ��� ��������. ������������ ���������.

___12. � index.php �����:
<?php get_header() ?>
<?php get_footer() ?> 
��� ����������� ��������������� ������.

___13.������� �����
header.php  
footer.php

___14. � ���� header.php
������ �� index.html ��� � ������ ������ �� �������������� ���� </header>

___15. � ���� footer.php 
������ �� index.html ��� � ������ ���� footer �� ������ ����� ����

___16. � index.php
������ �� index.html ��������� ��� 

___17. ��������� � ����� ������� ��� ����������� �����

___18. ������� ���� functions.php ��� ����������� ����� � ������ � ������ ����������

___19. � ����� functions.php:

����������� ������� ������ ������ ������.
<?php 

	echo get_stylesheet_uri();

� ������� ����� �������� ���������� ����� ����.

___20. ����� � ����� functions.php ��������� ��� (�������� ���):

<?php

add_action( 'wp_enqueue_scripts', 'my_scripts_method' );
function my_scripts_method(){
	wp_enqueue_script( 'newscript', get_template_directory_uri() . '/js/custom_script.js');
}

��� ���� ��� �� ����� 
echo get_stylesheet_uri()
� ��� ����� �������

___21. ����� "<?php" � ����� "add_action" �������:
 
define("B_THEME_ROOT", get_template_directory_uri()); - ���������� ����� ������. B_THEME_ROOT ��� ���������, 
������� ����� ����� ������������. ��� �.�. ���������� ���. ��� ��������� ����� ������������ ��� ������ ����������� 
���� css � ��. �� ������� �����.

___22. ����� - ��������� ����� ������ � ���� ������������ ����� �����:

define("B_CSS_DIR", B_THEME_ROOT . "/css");
define("B_JS_DIR", B_THEME_ROOT . "/js");
define("B_IMG_DIR", B_THEME_ROOT . "/img");

___23. � add_action ������ 'my_scripts_method' ���������� ���� ��������.
� function (����� ���) ����� ��� ���������������.
� �������: "up_style"

___24. � function up_style ���������� �����, ����� ����� ��� (������ � ���������� �� �������� ���).
��� ���� �������� ����  'main' 'media' 'animate' - ��� ��� ������������ �������� ��������. ����� - ���� ���������� 
� ��� ����� - ���������� ����.

 //add style
   function up_style(){
      wp_enqueue_style( 'bootstrap', B_CSS_DIR . '/bootstrap/bootstrap.min.css');
      wp_enqueue_style( 'main', B_CSS_DIR . '/style.css');
      wp_enqueue_style( 'mediacss', B_CSS_DIR . '/media.css');

        }

___25. ���������� �������������� JS Qerry is WP � ���������� ��� �� � function, ����� ������ �� ���������� �������: 

wp_deregister_script("jquerry");

___26. ����� ���������� ��� ����� js � functions ��� �� ����� ���������� jquerry.
� ����� - ������������ ���� jquerry, �� ����� ������:

 wp_deregister_script("jquery");
      wp_enqueue_script( 'jquery', B_JS_DIR . '/jquery/jquery.min.js');
      wp_enqueue_script( 'bootstrap', B_JS_DIR . '/bootstrap/bootstrap.js');
      wp_enqueue_script( 'magnific-popup', B_JS_DIR . '/magnific-popup/magnific-popup.min.js');
      wp_enqueue_script( 'parallax', B_JS_DIR . '/parallax/parallax.min.js');
      wp_enqueue_script( 'page-scroll-to-id', B_JS_DIR . '/page-scroll-to-id/jquery.malihu.PageScroll2id.js');
      wp_enqueue_script( 'wow', B_JS_DIR . '/wow/wow.min.js');
      wp_enqueue_script( 'isotope', B_JS_DIR . '/isotope/isotope.pkgd.min.js');
      wp_enqueue_script( 'countUp', B_JS_DIR . '/countUp/jquery.countup.min.js');
      wp_enqueue_script( 'waypoints', B_JS_DIR . '/waypoints/jquery.waypoints.min.js');
      wp_enqueue_script( 'functions', B_JS_DIR . '/functions.js');
      wp_enqueue_script( 'send', B_JS_DIR . '/send.js');
}

___27. ��������� � header.php � ������� ��������� ��� �����������.
<!-- Bootstrap -->
	<link rel="stylesheet" href="css/bootstrap/bootstrap.min.css">

	<link rel="stylesheet" href="css/style.css?014">

	<link rel="stylesheet" href="css/media.css?015">


� �������������� ������ ����:
<?php wp_head(); ?>


___28. �� �� ����� ���������� � footer.php ����� </body>
<?php wp_footer(); ?>

___29. � header.php ����� ������ ������ img ��������� ���:
<?php echo B_IMG_DIR ?>/first_screen_bg.jpg" (����� / - ��� ����)

___30. ������������ ����.
� ����� functions.php
� ����� ����� ���� ��� ��� ��� ����������...

add_action( 'after_setup_theme', 'theme_register_nav_menu' );
function theme_register_nav_menu() {
register_nav_menu( 'primary', 'Primary Menu' );
}

���
'after_setup_theme' - ������������ ������� ��� ��������,
'theme_register_nav_menu'- �� ��� ��� ���������� ��� function
function theme_register_nav_menu = ����� function ����� ������ ��������, 
�� ��, ��� ���� ���� ������ ���������� theme_register_nav_menu.
primary = �� ��� ��� ���������� � ���� ������, ���� id ��� ������.
Primary Menu = �� ��� ��� ����� ���������� � ������� 

___31. � ������� ����� ��������� ����, ������ � ��. �� ������� ��������������� ����, 
��� �� ������� �������������� ��� ����.
�� ������� ���������� ��������� �������� �� �������� ����, � �������� ��� ����������� - 
� ����� ������ ������ ���������
 

___32. ����� ����, ��� ���� ����������������, 
������� ����� � header.php � � div ��� ���������� ��� ���� (���� <ul>)
������� ���
<?php wp_nav_menu([
'theme_location'  => '',
]); ?>

��� 'theme_location'  => '', '�����, ������ ������� ����. 
� functions.php ���� ����� � top (�������� ����� ����������� ��������)

����� ����� � ��� �� ������� �������� 'container'       => 'null', 
��� ���������� ������ � ��������������� �� ���� ������ css. 
��� ���� �������� ����� ���� ������ - ��. ������������ 

___33. ��������� ������ ul.
� ������ li, ������� ���� ����� lamb � ��� ������ � JS ��������.
������ li ����� �������������� �� �������������, ��� � ������ ��������, ����� ��.


___34. � ������� - ����������� ����.
��� ��� ���������� ������� ������ - ������ ������ � ���� ������ # � ��� ������� - �������� ������� ������
� ������� #about 
�������� ����� id, ������ ������� ���� � ����


___35. ����� ������� ������ ���� � function.php ��������� ���
add_action( 'after_setup_theme', 'mobile_menu' );
function mobile_menu() {
register_nav_menu( 'primary', 'Primary Menu' );
}

� ������� WP ���� ������� ����� ����.

� � header - �������� ��� 
<?php wp_nav_menu([
'theme_location'  => 'top',
'container'       => null
]); ?>
������ ���������������� ���������� ������

___36.
� header ��������:
<html <?php bloginfo( "language" ); ?>>
<head>
<meta charset="<?php bloginfo( "charset" ); ?>">
<title><?php bloginfo( "name" ); ?></title>
<meta name="description" content="<?php bloginfo( "description" ); ?>">

����� ��� ��� ����� ������������ ����� WP

___37. ������� WP

1 = All in One SEO Pack
https://ru.wordpress.org/plugins/all-in-one-seo-pack/

2 = Broken Link Checker
https://ru.wordpress.org/plugins/broken-link-checker/

3 = Contact Form 7
https://ru.wordpress.org/plugins/contact-form-7/

4 = Imagify � WebP & Image Compression and Optimization
https://ru.wordpress.org/plugins/imagify/

5 = Jetpack �� WordPress.com
https://ru.wordpress.org/plugins/jetpack/

6 = Migrate Guru: Migrate & Clone WordPress Free
https://ru.wordpress.org/plugins/migrate-guru/

7 = WordPress Gallery Plugin � NextGEN Gallery
https://ru.wordpress.org/plugins/nextgen-gallery/

8 = UpdraftPlus WordPress Backup Plugin
https://ru.wordpress.org/plugins/updraftplus/

9 = W3 Total Cache
https://ru.wordpress.org/plugins/w3-total-cache/

10 = WooCommerce
https://ru.wordpress.org/plugins/woocommerce/

11 = Yoast SEO
https://ru.wordpress.org/plugins/wordpress-seo/

12 = Download Monitor
� �������� WP

___38. ����������� ����� Download Monitor ���� "��������" ��������� � �������� �����.
����������� �������� �� ���� ��� ��� ��������������� �������� ���� ������, � �� ����.

����� - �������� ��������������� ���� � ����� - �������� URL.	
� ����� - ������������.
����� ������������ ������� � ��������, ������� ����� ������ �������� ������ � header.php
echo do_shortcode('[somename]'); 

�� ����, ������ 

<p><a href="download/CV.doc" download>Download CV</a></p>

����� 

<p><a href=""><?php echo do_shortcode('[download id="21"]'); ?></a></p>
��� [download id="21"] ��� ������������� ������� �� ������� WP

���� ���� ������ �������, �� ������� ������.

___39. ������������ ��������� ��������.
������ ���� :
<h1 class="logo"><a href="index.html">B.</a></h1>

������ �� �����
<h1 class="logo_img"><a class="none" href="">Brendon - Personal HTML Template For Creative Professionals</a></h1>

����� - � functions.php ��������

add_theme_support( 'custom-logo', [
	'height'      => 190,
	'width'       => 190,
	'flex-width'  => false,
	'flex-height' => false,
	'header-text' => '',
] );

��� �������� ��� ����, ����� �� �������� ������ ����������� 

add_theme_support( 'custom-logo');

�� ������� - "������� ���", "���������", "�������� �����", "�������"

� header.php ��� ��� ��� ��� �������� �������� �����:
<?php if(has_custom_logo()) {
the_custom_logo();
} else { ?>
<h1 class="logo_img"><a class="none" href="">Brendon - Personal HTML Template For Creative Professionals</a></h1>
<?php } ?>

��� ���� �������� �� ������� the_custom_logo, ������� ���� �� ������� � ���� ��� ���, �� 
����������� ��� ��� �� ������.

___40. ��������� �������� � �������

add_theme_support( 'custom-header', array(
         'width'         => 980,
         'height'        => 60,
         'default-image' => get_template_directory_uri() . '/images/header.jpg',
         'uploads'       => true,
      ) );

���� �����-� ��������� ���������� � �������, �� ��������� ����� �� ����.
� �������:
add_theme_support( 'custom-header', array(
'default-image' => get_template_directory_uri() . '/images/header.jpg',
'uploads'       => true,
      ) );
 
���� �������� �� ����������� - ��������� ������� ����������� � �������� �������.
(header.php)

� �������� ������ ������ ��������� ���
<?php header_image(); ?>

___41.����������� ������ ����. ��� ���� ����� - ����� ���.

___ 41.1

����� ���� ����� �������� � �������� ������:

add_action( 'init', 'register_post_types' );
   function register_post_types(){
	   register_post_type('hello', array(
		'labels' => array(
			'name'               => '�����������', // �������� �������� ��� ���� ������
			'singular_name'      => '�����������', // �������� ��� ����� ������ ����� ����
			'add_new'            => '�������� �����������', // ��� ���������� ����� ������
			'add_new_item'       => '���������� �����������', // ��������� � ����� ����������� ������ � �����-������.
			'edit_item'          => '�������������� �����������', // ��� �������������� ���� ������
			'new_item'           => '����� �����������', // ����� ����� ������
			'view_item'          => '�������� �����������', // ��� ��������� ������ ����� ����.
			'search_items'       => '������ �����������', // ��� ������ �� ���� ����� ������
			'not_found'          => '�� �������', // ���� � ���������� ������ ������ �� ���� �������
			'not_found_in_trash' => '�� ������� � �������', // ���� �� ���� ������� � �������
			'parent_item_colon'  => '', // ��� ��������� (� ����������� �����)
			'menu_name'          => '����������� � �������', // �������� ����
		),
		
		'public'              => false,
		'show_ui'             => true,
		'menu_icon'           => "dashicons-editor-contract", 
		'supports'            => array( 'title', 'editor' ), // 
		) );
}


����� ����� 

function getHello() {
   
   $posts = get_posts( array(
	'orderby'     => 'date',
	'order'       => 'ASC',
	'post_type'   => 'hello',
) );
   return $hello
}

��� ����� ������ �������

function getHello() {
   
   $args = array(
	'orderby'     => 'date',
	'order'       => 'ASC',
	'post_type'   => 'hello',
);
   return get_posts($args);
}

� header ����� 
<div class="content_name">
<p class="hello">WELCOME. I AM</p>
<p class="name">BRENDON WILLIAMS</p>
</div>

���������� �������� ������� 
<?php foerach (getHello() as $post): ?>

����� ��� ������

�

<?php endforeach; ?>

�����

--- ���������� � header

<?php foreach (getHello() as $post): ?>
<div class="content_name">
<p class="hello">WELCOME. I AM</p>
<p class="name">BRENDON WILLIAMS</p>
</div>
<?php endforeach; ?>	
---

����� ������ WELCOME. I AM ���������� �������� ������� 
<?php echo $post->post_title;>

��� post_title � post_content ����� ����� ����� ����� var_dump.

������ BRENDON WILLIAMS
�����������

<?php echo $post->post_content;>

� ����� ���� ����� ��������� ���

<?php foreach (getHello() as $post): ?>
<div class="content_name">
<p class="hello"><?php echo $post->post_title; ?></p>
<p class="name"><?php echo $post->post_content; ?></p>
</div>
<?php endforeach; ?>	

��� ��� ������ � functions.php ������� �������� ���:

function getHello() {
   
   $args = array(
	'orderby'     => 'date',
	'order'       => 'ASC',
	'post_type'   => 'hello',
);
   return get_posts($args);
}

42.2 ��� �������� ���������� ����� ����� �������� ����� ������.

������ - advanced custom felds

� ������� ���������� "������ �����"

����� - ��������

������ �������� � ��� ������ (���������� � ��.)

����� - �������� ����, ����� ��������� � �����������.

� ����� "����������� � �������" ��������� ����� ����
  

��� ��������� ����� � ����� �������� ��� � functions php:

function getHello() {
   
   $args = array(
	'orderby'     => 'date',
	'order'       => 'ASC',
	'post_type'   => 'hello',
);
$bannerTexts = [];

   foreach (get_posts($args) as $post) {
      $bannerText = get_fields($post->ID);
      $bannerText["title"] = $post->post_title;
      $bannerText["content"] = $post->post_content;
      $bannerTexts[] = $bannerTexts; 
   }
   return $bannerTexts($args);
}

42.3 � header.php ������� ��������������� ���
<?php foreach (getHello() as $bannerText): ?>
<div class="col-md-12 col-sm-12 col-xs-12">
<div class="content_name">
<p class="hello"><?php echo $bannerText["title"]; ?></p>
<p class="name"><?php echo $bannerText["content"]; ?></p>
</div>
</div>
<div class="col-md-12 col-sm-12 col-xs-12">
<div class="content_prof">
<p><span><?php echo $bannerText["description"]?></span></p>
</div>
</div>
<?php endforeach; ?>

�� ���� ������ ���������� $post �������� ���������� $bannerTexts

___43. ���������� ������ ����� ������.
��������� � ������� ������ ����� � � ���� ������ ����� ���� ������
<?php the_field("�������� ����, ������� ���� � �������") ?>  

___44. ���� �� �������� ������� � JS �� �������
������� ��� ��������� ��������, �� ���� ��������� ����� ���� "use strict";
$(window).on( 'load', function() {

$('.counter').countUp({
	'time': 2000,
	'delay': 10
  });

...___...

___45. �������� ������� ���� �� WP

������������ ������� remove_action().

� ����� function.php
������� ��������� ������������� ��� 

add_action("wp_head","clearFunc", 1 );

function clearFunc(){
   add_filter( "xmlrpc_enabled", "__return_false" );
   remove_action( "wp_head", "feed_links" );
   remove_action( "wp_head", "feed_links_extra" );

   remove_action( "wp_head", "rsd_link" );
   remove_action( "wp_head", "wlwmanifest_link" );
   remove_action( "wp_head", "wp_generator" );

   remove_action( "wp_head", "wp_shortlink_wp_head" );
   remove_action( "wp_head", "adjacent_posts_rel_link_wp_head" );

   add_filter( "rest_enabled", "__return_false");
   
   remove_action( "xmlrpc_rsd_apis", "rest_output_rsd" );
   remove_action( "wp_head", "rest_output_link_wp_head" );
   remove_action( "template_redirect", "rest_output_link_header" );
   remove_action( "auth_cookie_malformed", "rest_cookie_collect_status" );
   remove_action( "auth_cookie_expired", "rest_cookie_collect_status" );
   remove_action( "auth_cookie_bad_username", "rest_cookie_collect_status" );
   remove_action( "auth_cookie_bad_hash", "rest_cookie_collect_status" );
   remove_action( "auth_cookie_valid", "rest_cookie_collect_status" );
   remove_action( "rest_authentication_errors", "rest_cookie_check_errors");

   remove_action( "init", "rest_api_init" );
   remove_action( "rest_api_init", "rest_api_default_filters" );
   remove_action( "parse_request", "rest_api_loaded" );

   remove_action( "rest_api_init", "wp_oembed_register_route" );
   remove_filter( "rest_pre_serve_request", "_oembed_rest_pre_serve_request");

   remove_action( "wp_head", "wp_oembed_add_discovery_links");
}

��� ����� ��������� ����� ����������� ���������� ���� PHP � functions.php
  
___46. ���������� ������� WP.

   46.1 �������� ������� ����� �������. ������ -> �������
   ������ �������� � ����.

   46.2 �������� ��������. ������� ��� ����� ������� � ������� "�����" ��� ��� �������������
   ���� ��� ���������� ����� ������.

   46.3 ��� ��������� �� ����� ������� ����� ����� ������������� ����, ��� ����� ���������� 	id
�������. � ������� I_ID=7&post

   46.4 � index.html ������� ��������� �������� portfolio item, ������� ���� � �������� ����.
����� ���� item ��������������� � �������� �����.

������ � ��������� ��� �������� ���:

<div class="row">
	<div class="col-md-12 col-sm-12 col-xs-12">
		<div class="isotope_items row">
			<?php if (have_posts()) : query_posts( "cat=����� ID" );
			while(have_posts()) : the_post(); ?.>
			<!-- Item -->
			<a href="<?php the_post_thumbnail_url(array(360,360) ) ?> class="single_item link aplication col-md-4 col-sm-6 wow fadeInUp" data-wow-delay="1.8s">
			<img src="<?php echo B_IMG_DIR ?>/portfolio/work-6.jpg" alt=""> 
			</a>

			<?php endwhile; endif; wp_reset_query(); ?>
			<!-- Add new image -->
		</div>
	</div>
</div>

������ 360 �� 360 ������������ �� ������.


   46.5 �������� ����� ������ ����� ������� WP -> ������� ��������� ��� ����� ������ (���������) -> 
������� ���� "���������� ����������� ������" � ���� "����������� ������" -> ��������� ��� �����������
�������� -> ������������ ������.

   46.6 ����� ��� ������� �� �������� ��������� ������� �������� ���������� �������� ��������� ���:
� �������, ������ 
	<img src="<?php echo B_IMG_DIR ?>/portfolio/work-1.jpg" alt=""> 

��������:

<img src="<?php $large_image_url = wp_get_attachment_image_src( get_post_thumbnail_id(), "large" );
echo $large_image_url[0]; ?>" alt="">


46.7 ��� ���������� �������� �� �������� ���������� ����������� �����. ��� ����� ���� � ���� ��� ������� ��� �� ����� �����.
����� ����������� � ������� � ��������, ��� ���������� ������ �� enter.
� ���� ������ ����� �� ��������� - � ��������, ��� ��� development

<a href="<?php the_post_thumbnail_url( array(360,360) ); ?>"
class="single_item link development col-md-4 col-sm-6 wow fadeInUp" data-wow-delay="0.3s">

���������� ��������:
<?php $tags = wp_get_post_tags( $post->ID );
if ($tags) {
foreach ($tags as $tag){
echo "" . $tag->name;	
}}?>

�� ����, ���� � ����� ����� �����

	<div class="isotope_items row">
<?php if (have_posts()) : query_posts( "cat=4" );
	while(have_posts()) : the_post(); ?>
	<!-- Item -->
	<a href="<?php the_post_thumbnail_url( array(360,360) ); ?>" class="single_item link col-md-4 col-sm-6 wow fadeInUp 
	<?php $tags = wp_get_post_tags( $post->ID );
	if ($tags) {
		foreach ($tags as $tag){
		echo ' '. $tag->name;	
}
}
?>"
	data-wow-delay="0.3s">
	<img src="<?php $large_image_url = wp_get_attachment_image_src( get_post_thumbnail_id(), "large" );
	echo $large_image_url[0]; ?>" alt=""> 
	</a>

<?php endwhile; endif; wp_reset_query(); ?>
</div>

47. ������� ����� ���������� ����� �������
Contact Form 7 
� Easy WP SMTP (��� �������� ����� �� ����� ��������)

� �������� ����������� 

	<?php echo do_shortcode( '[contact-form-7 id="50" title="���������� ����� 1"]' ) ?>

��� [contact-form-7 id="50" title="���������� ����� 1"] ������������ � WP � ����

<fieldset class="wow zoomIn padding_r">
[text* name1 id:name1 placeholder "Name"]
</fieldset>
<fieldset class="wow zoomIn padding_l">
[email* email id:email placeholder "E-mail"]
</fieldset>
<div class="textarea_block wow zoomIn">
[textarea* message id:message placeholder "Message..."]</textarea>
<div id="messegeResult" class="wow zoomIn">
[submit id:button "SEND A MESSAGE"]
</div>

� ���������� ������� ������������ WP �������

48. ����������� �����.

� ���������� -> ������, ������� "�� ������� �������� ����������" - "���� ��������� ������".

����� - ������� ����� ��������, ���� �������� � ����� - 
����������� ����� ������ ����������� � ������� � Index.php � ������ �����
� ������ (��, ������� ����� �� ����), ������� ����� � ��� href �� ���, ������� ��� � WP.

� �������, http://wpdev/blog/

48.1 ��� ������������ �������� ����� ������� ����� ���� php, � ������� ��������� ��������
����� �� index.

���������� ����� � ����� ������� � � �����

<?php get_header(); ?>

<?php get_footer(); ?> 

48.2 ����� �� ����� �������� ��������� ����� ������� ������� ����� ����, � ������������ ��������� header-...php

��������� �������� �� header.php

��������� ��������������� �������� �� �������� ����������� ��������
� �������, <header id="home" class="blog_head_bg">.

�������� ����� ������ �� ���, ��� �� �������� - ����� � ����������� ��������.

 <div class="content_head">
                <div class="container">
                    <div class="row">
                        <div class="col-md-12 col-sm-12 col-xs-12">
                            <div class="content_head_txt">
                                <p>MY THOUGHTS</p>
                            </div>
                        </div>
                        <div class="col-md-12 col-sm-12 col-xs-12">
                            <div class="content_bottom_txt">
                                <p>Take a look and share your opinion.</p>
                            </div>
                        </div>
                    </div><!-- end row -->
                </div><!-- end container -->
            </div>
            
������
            
<div class="content_head">
    <div class="container">
        <div class="row">
            <div class="col-md-12 col-sm-12 col-xs-12">
                <div class="content_name">
                    <p class="hello">WELCOME. I AM</p>
                        <p class="name">BRENDON WILLIAMS</p>
                        </div>
						</div>
						<div class="col-md-12 col-sm-12 col-xs-12">
                        <div class="content_prof">
<p><span>The best designer ever.</span></p>
    </div>
	</div>
        <div class="col-md-12 col-sm-12 col-xs-12 clearfix">
        <div class="content_download">
        <p><a href="download/CV.doc" download>Download CV</a></p>
    </div>
	</div>
</div>

48.3 ��� ���� � <?php get_header(); ?> ������� �������, ��� ��������� ������
����� �����.

    <?php get_header('page.php'); ?>
    ��� ���� ����������� �������� �� header-page, � ������ page, ������ ���
header ���������� � ���� ����� ��������    

49. �������.

���������� ������� ����� ����. Sidebar.php
��������� ������� � ���� �� ��������������� �������, ������� ��.

� page.php �������� ���:

<?php get_sidebar(); ?>


49.1 ����� ���������� ���������������� sidebar � functions.php ����� �������
register_sidebar()

������ �������������, �������� � functions.php:

add_action( 'widgets_init', 'register_my_widgets' );
function register_my_widgets(){
	register_sidebar( array(
		'name'          => sprintf(__('Sidebar %d'), $i ),
		'id'            => "sidebar-$i",
		'description'   => '',
		'class'         => '',
		'before_widget' => '<li id="%1$s" class="widget %2$s">',
		'after_widget'  => "</li>\n",
		'before_title'  => '<h2 class="widgettitle">',
		'after_title'   => "</h2>\n",
	) );
}

49.2

����� ����������� �������� WP ��������� � ������� ������ "�������" �������������.

����� ����� ������� ����� ���� ��������� ������� � �������, ������� �� ������������� �������� ���������� ������������ ������� dynamic_sidebar(): 

    <?php dynamic_sidebar( $index ); ?>
��� ��� �������� � ������ sidebar.php �� ��� ���� ����� �� ��� � ��������, � �������, � ������ ��������� ����.

���� ������� �� ����� ����, ��  $index ����� �� ���������. ���� ���������, �� �������� ����� ���������, � ���� ID ������ �������� �� functions.php

49.3 ��� ���������� ��������, � ���������, ��������� � functions.php
��������� � ����: 

'before_widget' => '<li id="%1$s" class="widget %2$s">',
������ �� ��� ����� ������������ ������ �� ������������� ����.
'after_widget'  => "</li>\n",
� �����

� �������:
'before_widget' => '<div class="widget %2$s">',
'after_widget'  => "</div>\n",

���� ������� �������� � ������� ����, �� ��� ����� ��������� � after, � �������: 
'after_widget'  => '</div><div class="space x-small"></div>',

�����: 
'before_title'
���� ������� ������������ �������� ����� ���������, �� ��� ����������� �� ����.
� �������:

'before_title'  => '<h5 class="blog-text-uppercase">',

'after_title'   => "</h2>\n",
���������� � ����� ������ �� ���������� ���
'after_title'   => "</h5>\n",

49.4
����� ������� ����������� ������� �� �������.
��� ���� ����� ������� � ���� ���������� ���� ����� ��� ��������.

2 ������� ���������� ��� ������ ����:
- ����� ������� � functions.php
- ��������� ������ searchform.php

2� ������� ���������:

����� ������� get_search_form()

����:
����� �������� �� ����, ������������� WP ��� searchform �� ���������, ���������� ����:
<form role="search" ' . $aria_label . 'method="get" id="searchform" class="searchform" action="' . esc_url( home_url( '/' ) ) . '">
				<div>
					<label class="screen-reader-text" for="s">' . _x( 'Search for:', 'label' ) . '</label>
					<input type="text" value="' . get_search_query() . '" name="s" id="s" />
					<input type="submit" id="searchsubmit" value="' . esc_attr_x( 'Search', 'submit button' ) . '" />
				</div>
			</form>

� �������� ��� � searchform.php

����� �������� � ���� ���� 
' . 

    �� 

<?php

� ������������� 

. '

    ��
    
?>    

49.5
����� ������������ ������� ��������. 
�������� ��������� ������� �� searchform.php � �� ��� ���� � sidebar.php � ��� 
������������� ��������� � searchform.php �����������.

����� ��������� � ����� css ��� �������������, � �������, ������.

� �������:

.sidebar-menu .search-form .form-group:after {
  content: '';
  background-image: url(../img/search.svg);
  position: absolute;
  display: block;
  width: 13px;
  height: 15px;
  top: calc(50% - 7,5px);
  right: calc(50% - 8px);
  background-size: contain;
  background-repeat: no-repeat;
}

49.6
���� �������, ������������ WP � �������� �� ������������� ���� ����� ����� 
��������� ��������, �������� ������� �� ������������� WP � style.css. ����� ���������� ��� � ��� � ��� � ������������.
� �������, ���� � ������� ���� ����� �����, � WP ���������� ���� .widget_categories �� ����� ��������������� ����� �������� ���, ��� ���������� WP.

50. ��������� �����.

50.1 ��������� �������� page.
����� ��������������� ����. 
��������� ��� ������ 1 ������, ��������� ����� ������������� ����� php.

� ����� ���� �������� ����� ��������� �������������� ���:

<!-- BLOG CONTENT -->
						<div class="col-md-9">
							<div class=" blog-content">
								<div class="col-md-6 col-sm-6">
									<div class="content-box">
										<div class="blog-img-frame">
											<a class="blog-img" href="blog-single.html">
												<img src="img/blog-grid/blog-grid-1.jpg" alt="">
											</a>
										</div>

										<div class="content">
											<a href="blog-single.html">
												<h4 class="blog-text-uppercase">Creating your own website</h4>
											</a>
											<p class="block-date">Brendon Williams - 27 January 2017</p>

											<p>Hello, I�m Brendon, Creative Designer & User Experience Engineer based in New York � I create awesome web digital products. I know you can too.</p>
											<div class="blog-buttons">
												<a href="blog-single.html">read more
													<i class="fa fa-long-arrow-right"></i>
												</a>
											</div>
										</div>
									</div>
								</div>

50.2 ����� ���� �����, �� �� �������, � ��� ��� ����� ���������� ������ ����� ��������:

<?php if (have_posts()){ while (have_posts()) {the_post(); ?>
(...����� ���� � ������...)

<?php } /*����� while*/?>
<?php } /*����� if*/?>

C �������� ���� �� ����� ����� ���� 

<div class="col-md-9">
    <div class=" blog-content">
    
50.3 ���� ��� ���� �� ��������� ������ ����, �� ����� ������ ����� ���������� 
$query, ������� �������� ������ ��������� � ���� ������... 

���:
- WP_Query ��� ���������� �� �������.

- 'post_per_page' => '4', - ��� ���������� ����-������� �� ��������. ����� ��� ����� �������� � ������� - ��������� - ������.

�� ������� ��������� ����������. ���� ���������� ����� ������������� ���������� ������� ������� ��� �������� ����� ������� �� ����.

- 'category_not_in' => '7', - �������, ��� ������ �� ������� ��� ������� ���� 7 (��� ����� ����, ������� ��� ����������� WP - ��. ���� ��� ��� ������) �� �������� � ���� ��� ��� ��� ����� ������ �������.

- 'paged' => get_query_var('paged') ?: 1); - ���������� ��� ���������.




...�� ��� ������� ������� � ��������� ���� � ������ �������

	<div class="col-md-9">
							<div class=" blog-content">
						<?php 
							$query_args = array(
								'post_per_page' => '4',
								'category_not_in' => '7',
								'paged' => get_query_var('paged') ?: 1
								);
							?>			
							<?php wp_reset_query(); $query = new WP_Query($query_args); ?>
							<?php if ($query->have_posts()){while ($query->have_posts()) {$query->the_post();?>
							
								<div class="col-md-6 col-sm-6">
									<div class="content-box">
										<div class="blog-img-frame">
											<a class="blog-img" href="blog-single.html">
												<img src="img/blog-grid/blog-grid-1.jpg" alt="">
											</a>
										</div>

										<div class="content">
											<a href="blog-single.html">
												<h4 class="blog-text-uppercase">Creating your own website</h4>
											</a>
											<p class="block-date">Brendon Williams - 27 January 2017</p>

											<p>Hello, I�m Brendon, Creative Designer & User Experience Engineer based in New York � I create awesome web digital products. I know you can too.</p>
											<div class="blog-buttons">
												<a href="blog-single.html">read more
													<i class="fa fa-long-arrow-right"></i>
												</a>
											</div>
										</div>
									</div>
								</div>
								<?php } /*����� while*/?>
								<?php } /*����� if*/?>
                                                  
50.4               

��� ��������� ������ ����� ������ ������� ������ ���� a href 
<a class="blog-img" href="blog-single.html">
� ������� ����� - ���:

<a class="blog-img" href="<?php the_permalink(); ?>">

������ �������� 
<img src="img/blog-grid/blog-grid-1.jpg" alt="">
������� ���
<?php the_post_thumbnail (); ?>

������� ����������� ��� ���������� ����� ����� ( array(360,360) ) � ����� ����� ��� ����� �������. �� ����,
<?php the_post_thumbnail ( array(371,278)); ?>

��� ��������� ���������� - �������� ��� � ����������� �� ��� 
<?php the_title(); ?>

�� ����, � �����: <h4 class="blog-text-uppercase"><?php the_title(); ?></h4>

��� ��������� ������ - ��� � �������
<?php the_author(); ?>

��� ��������� ����...
<?php echo get_the_date('n-j-Y'); ?>

��� ��������� ������ ����� - �������� �������� �� ���:

<?php the_content(); ?>

50.5 ���������

���������� ����������� ����� ���� �����

<?php } /*����� while*/?>
<?php } /*����� if*/?>

�� ���� 

<?php } /*����� while*/?>
<?php the_post_pagination(); ?>
<?php } /*����� if*/?>

����� ��� ��������� �� "�������" ���������, �� � ����� ������� ������:

<?php } /*����� while*/?>
<?php 
    $wp_query = $query;
    the_post_pagination(); ?>
<?php } /*����� if*/?>

��� ��� ���� ������� ����������������

<!--<div class="col-md-12">
	<nav class="box-pagination text-center">
        <ul class="blog-pagination">
		<li class="back arrow"><a href="#">back</a></li>
		<li class="active">1</li>
		<li><a href="#">2</a></li>
		<li><a href="#">3</a></li>
		<li><a href="#">4</a></li>
		<li><a href="#">5</a></li>
		<li><a href="#">6</a></li>
		<li class="next arrow"><a href="#">next</a></li>
		</ul>
    </nav>
</div> -->


����� ���� ��������� �� ���������, � �������� - ������� ��� 
<?php the_content(); ?>
�������� �����
<?php the_excerpt(); ?>

50.6 ��� ��������� ���������:

� ��� <?php 
    $wp_query = $query;
    the_post_pagination(--� ��� �����--); ?>

    ��������:
$args = array(
	'show_all'     => false, // �������� ��� �������� ����������� � ���������
	'end_size'     => 1,     // ���������� ������� �� ������
	'mid_size'     => 1,     // ���������� ������� ������ �������
	'prev_next'    => true,  // �������� �� ������� ������ "����������/��������� ��������".
	'prev_text'    => __('� Previous'),
	'next_text'    => __('Next �'),
	'add_args'     => false, // ������ ���������� (���������� �������), ������� ����� �������� � �������.
	'add_fragment' => '',     // ����� ������� ���������� �� ���� �������.
	'screen_reader_text' => __( 'Posts navigation' ),
);

� ��������� ��� �����, ��������

<?php 
    								$wp_query = $query;
									the_posts_pagination(
									$args = array(
                                    'show_all'     => true, // �������� ��� �������� ����������� � ���������
									'prev_next'    => true,  // �������� �� ������� ������ "����������/��������� ��������".
									'prev_text'    => 'BACK',
									'next_text'    => 'NEXT'
									
									));
?>

�������� h2 �� ���������, ������� ������������ �������������.

� functions php �������� ������ 

add_filter('navigation_markup_template', 'my_navigation_template', 10, 2 );
function my_navigation_template( $template, $class ){
	/*
	��� �������� �������:
	<nav class="navigation %1$s" role="navigation">
		<h2 class="screen-reader-text">%2$s</h2>
		<div class="nav-links">%3$s</div>
	</nav>
	*/
	
����� ������� �������� ��� �� functions.php � ��� ���, ������� ��� � ������.

<div class="col-md-12">
	<nav class="box-pagination text-center navigation %1$s" role="navigation">
    <div class="nav-links">%3$s</div>
   </nav>
   </div>

��� ����, ���� ����������� ����� ���� - ��� ��������� ���������, ���� � ������� ��� � nav ���� ����� � ������, �� � ������ nav ��� ����� "navigation %1$s" �� ��� ���������. 

	
���� � �������� �������, ��� ��������� �������������� ����� a, � � ��� ����� li, �� ������� �������� ��� �������� ������� pagination_links � ������������ ����� ��������� ���.

� �������, type ������ ������������� ���, � ������� �������� �������������� ������� ���������. �� ����, �������� � page.php

type - list.

<?php 
    								$wp_query = $query;
									the_posts_pagination(
									$args = array(
										'show_all'     => true, // �������� ��� �������� ����������� � ���������
										'prev_next'    => true,  // �������� �� ������� ������ "����������/��������� ��������".
										'prev_text'    => 'BACK',
										'next_text'    => 'NEXT'
										'type'         => 'list'
									)); 
									?>

���� � ������� ���� ����� "active" - ��� ������ ������� ������ �� "current" � ������ �������!!!

����� ������ ����������� ����� ��������� �� ������ ������� ��������� ���� class-wp-widget-categories

��� � ���� 	$cat_args = array(
			'orderby'      => 'name',
			'show_count'   => $c,
			'hierarchical' => $h,
		);
		
		�������� 
		
			$cat_args = array(
			'orderby'      => 'name',
			'show_count'   => $c,
			'hierarchical' => $h,
			'exclude' => '��� ������� ���� �������',
		);


����� - ������� ���� category.php 
� ���� ��������� �������� ����� ������ � ������� ���� �� ����. 
��� ���� ��� ���� ���������, ������� ��� ����� ��� ����, ����� ������� �� ������ ��������.

<!-- BLOG CONTENT -->
<div class="col-md-9">
							<div class=" blog-content">
						<?php 
							$query_args = array(
								'post_per_page' => '4',
								'category_not_in' => '4',
								'paged' => get_query_var('paged') ?: 1
								);
						?>			
                                <?php if (have_posts()){while (have_posts()) {the_post();?>
								<div class="col-md-6 col-sm-6">
									<div class="content-box">
										<div class="blog-img-frame">
											<a class="blog-img" href="<?php the_permalink(); ?>">
											<?php the_post_thumbnail ( array(371,278)); ?>
											</a>
										</div>

										<div class="content">
											<a href="<?php the_permalink(); ?>">
												<h4 class="blog-text-uppercase"><?php the_title(); ?></h4>
											</a>
											<p class="block-date"><?php the_author(); ?> - <?php echo get_the_date('j F Y'); ?></p>

											<?php the_content(); ?>
											<div class="blog-buttons">
												<a href="<?php the_permalink(); ?>">read more
													<i class="fa fa-long-arrow-right"></i>
												</a>
											</div>
										</div>
									</div>
								</div>
								<?php } /*����� while*/ ?>
								<?php 
    								the_posts_pagination(
									$args = array(
										'show_all'     => true, // �������� ��� �������� ����������� � ���������
										'prev_next'    => true,  // �������� �� ������� ������ "����������/��������� ��������".
										'prev_text'    => 'BACK',
										'next_text'    => 'NEXT',
										'type'         => 'list',
									)); 
									?>
								<?php } /*����� if*/ ?>
							
								<!-- PAGE NUMBER -->
								<!--<div class="col-md-12">
									<nav class="box-pagination text-center">
										<ul class="blog-pagination">
											<li class="back arrow"><a href="#">back</a></li>
											<li class="active">1</li>
											<li><a href="#">2</a></li>
											<li><a href="#">3</a></li>
											<li><a href="#">4</a></li>
											<li><a href="#">5</a></li>
											<li><a href="#">6</a></li>
											<li class="next arrow"><a href="#">next</a></li>
										</ul>
									</nav>
								</div> -->
							</div>
						</div>
						<!-- BLOG SIDEBAR -->
						<div class="col-md-3">
							<?php get_sidebar(); ?>
						</div>
					</div>
				</div>
			</div>
			<!------ END BLOG WRAPPER ------>
		</div>
		<!-- / -->
	</section>

<?php get_footer(); ?> 


50.7

��� ����������� ������ ������� search.php � ����������� ���� ��� ��������� �� category.php.

?php get_header('page'); ?>

<section class="blog-section blog-section-bg">

        <div class="breadcrumb">
            <nav class="container">
                <ul>
                    <li><a href="index.html">home</a></li>
                    <li class="active">blog</li>
                </ul>
            </nav>
        </div>
        <!--./Blog-breadcrumb--><!--  -->
        <div class="blog-wrapper">
            <!------ BEGIN BLOG WRAPPER ------>
            <div class="container">
                <div class="row">
                 	<div class="blog-list clearfix">
						<!-- BLOG CONTENT -->
						<div class="col-md-9">
							<div class=" blog-content">
						<?php 
							$query_args = array(
								'post_per_page' => '4',
								'category_not_in' => '4',
								'paged' => get_query_var('paged') ?: 1
								);
						?>			
								<?php if(have_posts()){ while (have_posts()) {the_post();?>
								<div class="col-md-6 col-sm-6">
									<div class="content-box">
										<div class="blog-img-frame">
											<a class="blog-img" href="<?php the_permalink(); ?>">
											<?php the_post_thumbnail ( array(371,278)); ?>
											</a>
										</div>

										<div class="content">
											<a href="<?php the_permalink(); ?>">
												<h4 class="blog-text-uppercase"><?php the_title(); ?></h4>
											</a>
											<p class="block-date"><?php the_author(); ?> - <?php echo get_the_date('j F Y'); ?></p>

											<?php the_content(); ?>
											<div class="blog-buttons">
												<a href="<?php the_permalink(); ?>">read more
													<i class="fa fa-long-arrow-right"></i>
												</a>
											</div>
										</div>
									</div>
								</div>
								<?php } /*����� while*/ ?>
								<?php 
    								the_posts_pagination(
									$args = array(
										'show_all'     => true, // �������� ��� �������� ����������� � ���������
										'prev_next'    => true,  // �������� �� ������� ������ "����������/��������� ��������".
										'prev_text'    => 'BACK',
										'next_text'    => 'NEXT',
										'type'         => 'list',
									)); 
									?>
								<?php } /*����� if*/ ?>
							
								<!-- PAGE NUMBER -->
								<!--<div class="col-md-12">
									<nav class="box-pagination text-center">
										<ul class="blog-pagination">
											<li class="back arrow"><a href="#">back</a></li>
											<li class="active">1</li>
											<li><a href="#">2</a></li>
											<li><a href="#">3</a></li>
											<li><a href="#">4</a></li>
											<li><a href="#">5</a></li>
											<li><a href="#">6</a></li>
											<li class="next arrow"><a href="#">next</a></li>
										</ul>
									</nav>
								</div> -->
							</div>
						</div>
						<!-- BLOG SIDEBAR -->
						<div class="col-md-3">
							<?php get_sidebar(); ?>
						</div>
					</div>
				</div>
			</div>
			<!------ END BLOG WRAPPER ------>
		</div>
		<!-- / -->
	</section>

<?php get_footer(); ?> 


��� ���� ���� searcform.php ������� ���������������� � ��������� ����:

<form role="search" method="get" id="searchform"  action="<?php echo home_url( '/' ) ?>">
	<div class="search-form  fullwidth">
	<div class="form-group">
		<input type="text" value="<?php get_search_query() ?>" name="s" id="s" placeholder="Enter keyword" class="form-control" />
		<input class="btn btn-search" type="submit" id="searchsubmit" value="�����" />
	</div>
	</div>
</form>

60. �������� �����
60.1 ��� �������� ��������� �������� ��� ������� �� �������� �����:
��������� ����. single.php
�� ��������������� ������� ���������� ��������.

����� � ����� �������� ��������������� �����.
<?php get_footer(); ?>
<?php get_header() ?>
���� ����� �������� ��� ����� ����������� ��� ����� (��. ����)

������� ������������ ����� 
<?php get_sidebar(); ?>

������ �������� ����:
    <img src="img/blog-list-1.jpg" alt="">
������������ ���
    <?php the_post_thumbnail(array(360,360) ) ?>
    ���� ����� 
    <?php echo get_the_date('j F Y'); ?>
    
    ��� ��������� ���������� ������������ ������� ������������ ���:
    
<?php comments_number('���� ��� ������������', '1 �����������', '% ������������'); ?>.</p>

��� ������ ��������:

    <?php the_content(); ?>
��� ������, ������� ������ ���� � ����� ������� ��� ������.
  <?php if (have_posts()) {while(have_posts()) {the_post(); ?>
  .........
  
    <?php } ?>
    <?php } ?>

60.2
�����������.
���������� ������� ���� comment.php

� ����� "comments" � ����� single.php ��������� ��� ������ ������� 
  <?php if(comment_open()) || get_comments_number()) {
                                    comments_template();
                                } ?>
� comment.php ��������� ��������� ������� ���:


<?php if (comments_open()) { ?>
  <h3 class="comments-caption"><a name="comments"><?php comments_number('�����������', '1 �����������', '% ������������'); ?> ��������� ������ "<?php the_title();?>"</a></h3>
    <?php if (get_comments_number() == 0) { ?>
      <ul class="list">
        <li>�������� ������ ����������� - ����� ��������</li>
      </ul>
    <?php } else { ?>
    <ol class="commentlist">
      <?php
        function verstaka_comment($comment, $args, $depth){
          $GLOBALS['comment'] = $comment; ?>
          <li <?php comment_class(); ?> id="li-comment-<?php comment_ID() ?>">
            <div id="comment-<?php comment_ID(); ?>">
              <div class="comment-author vcard">
                <div class="comment-meta commentmetadata" style="float: right;">
                  <span><?php printf(__('%1$s at %2$s'), get_comment_date(),  get_comment_time()) ?></span>
                </div>
                <?php echo get_avatar($comment,$size='74',$default='<path_to_url>' ); ?>
                <?php printf(__('@<cite class="fn">%s</cite> <span class="says">�����:</span>'), get_comment_author_link()) ?>
              </div>
              <?php if ($comment->comment_approved == '0') : ?>
                <em><?php _e('Your comment is awaiting moderation.') ?></em>
                <br>
              <?php endif; ?>
              <?php comment_text() ?>
              <div class="reply">
                <?php comment_reply_link(array_merge( $args, array('depth' => $depth, 'max_depth' => $args['max_depth']))) ?>
              </div>
            </div>
            </li>
      <?php }
        $args = array(
          'reply_text' => '��������',
          'callback' => 'verstaka_comment'
        );
        wp_list_comments($args);
      ?>
    </ol>
  <?php } ?>

  <?php
    $fields = array(
      'author' => '<p class="comment-form-author"><label for="author">' . __( 'Name' ) . ($req ? '<span class="required">*</span>' : '') . '</label><input type="text" id="author" name="author" class="author" value="' . esc_attr($commenter['comment_author']) . '" placeholder="" pattern="[A-Za-z�-��-�]{3,}" maxlength="30" autocomplete="on" tabindex="1" required' . $aria_req . '></p>',
      'email' => '<p class="comment-form-email"><label for="email">' . __( 'Email') . ($req ? '<span class="required">*</span>' : '') . '</label><input type="email" id="email" name="email" class="email" value="' . esc_attr($commenter['comment_author_email']) . '" placeholder="example@example.com" maxlength="30" autocomplete="on" tabindex="2" required' . $aria_req . '></p>',
      'url' => '<p class="comment-form-url"><label for="url">' . __( 'Website' ) . '</label><input type="url" id="url" name="url" class="site" value="' . esc_attr($commenter['comment_author_url']) . '" placeholder="www.example.com" maxlength="30" tabindex="3" autocomplete="on"></p>'
    );

    $args = array(
      'comment_notes_after' => '',
      'comment_field' => '<p class="comment-form-comment"><label for="comment">' . _x( 'Comment', 'noun' ) . '</label><textarea id="comment" name="comment" class="comment-form" cols="45" rows="8" aria-required="true" placeholder="����� ���������..."></textarea></p>',
      'label_submit' => '���������',
      'fields' => apply_filters('comment_form_default_fields', $fields)
    );
    comment_form($args);
  ?>
  <?php } else { ?>
  <h3>���������� ������� ��� ������ ��������</h3>
  <?php }
?>

�������� � �������� � ������� "�������" � ���/

� �������, ������ h3 - ��������  
<h4><?php comments_number('No Comments', '1 comment', '% comments'); ?> comments</h4>

����������� ������ � ���� <ol>

����� �������� - ���� �� ������� ����� ����������� ��������������, ������ ����:

<div class="comment-author vcard">
                    <div class="comment-meta commentmetadata" style="float: right;">
                    <span><?php printf(__('%1$s at %2$s'), get_comment_date(),  get_comment_time()) ?></span>
                    </div>
                    <?php echo get_avatar($comment,$size='74',$default='<path_to_url>' ); ?>
                    <?php printf(__('@<cite class="fn">%s</cite> <span class="says">�����:</span>'), get_comment_author_link()) ?>
                </div>
                <?php if ($comment->comment_approved == '0') : ?>
                    <em><?php _e('Your comment is awaiting moderation.') ?></em>
                    <br>
                <?php endif; ?>
                <?php comment_text() ?>
                <div class="reply">
                    <?php comment_reply_link(array_merge( $args, array('depth' => $depth, 'max_depth' => $args['max_depth']))) ?>
                </div>
                
������ � �������� ����� ���������� �����

<?php echo get_avatar($comment,$size=74,$default='<path_to_url>' ); ?>

������������� �� ����� � �������
<?php echo get_avatar($comment,64,'',array('class'=> 'media-object') ); ?>

��� ��������� ����� ������������, ����������� ����������� ����� get_comment_author_link() :

echo get_comment_author_link( $comment_ID );    

��� ������ ����������� ������������ ���: 

<?php comment_text();?>

��� ���� ������������ ���:

<?php echo get_the_date('n-j-Y'); ?>


����� ����������� ����� �������� ����� ��� ����.
����� comment_form.

����������� ����� ����� ����� ���� wp-include -> comment-template.php

60.3 
��� ���������� ������ Reply ������� �������� ������� 
comment_reply_link();

���:
<?php comment_reply_link(array_merge( $args, array('depth' => $depth, 'max_depth' => $args['max_depth']))) ?>

60.4
��� ��������, ���� ����������� ��� �����������, �� ���� ���������, ����� ����������� ���:

<?php if ($comment->comment_approved == '0') : ?>
    <em><?php _e('Your comment is awaiting moderation.') ?></em>
<br>

����� ���� 

<h5 class="media-heading blog-text-uppercase"><?php echo get_comment_author_link(); ?></h5>

61. ����� ��������� �� ������� �������� �����.

������� ������������ ��� 

	<?php 
					$posts = get_posts( array(
					'numberposts' => 5,
					'category'    => 0,
					'orderby'     => 'date',
					'order'       => 'DESC',
					'include'     => array(),
					'exclude'     => array(),
					'meta_key'    => '',
					'meta_value'  =>'',
					'post_type'   => 'post',
					'suppress_filters' => true, // ���������� ������ �������� ��������� SQL �������
				) );
				
				foreach( $posts as $post ){
					setup_postdata($post);
					// ������ ������ the_title() ...
				}
				wp_reset_postdata(); // �����

?>	

��� ���� ������ ���� 
$posts = get_posts( array(
��������� ��������, ������� ������� ������������ ���:

62. SEO �����������
62.1 ��������� ��������� SEO
--�������� �������� �� title, description, h1-h6;
--�������� 404;
--���������� ������������� �������;
--�������� �������� �����;
--��� �������� �����;
--������ js, css � ��������.

����� ������������ ������ Yoast SEO ��� ��������� ������ SEO-�����������

���������� ��������� �������� �������

��� ����������� ������������ �������
W3 total cache �  WP super Cache

63. ������ ����� �� ������.
- ���� ������������ �������;
- �������� �������������� ���������� WP;
- ������������ ��� remove_wp_version_strings;
- ��������� ����� �������� ������;
- �������� ����� �� ���������;
- ������������ ������� ������������;
- ������� ������ �����. "readme .html" \ "install.php";
- � ���� wp-config-php ������������ ������ ����� ������������;
- � ����� .htacess ��������� ������ � ���� ������ ������ � ��������� ��������� �������������;
