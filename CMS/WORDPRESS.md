___1. Устанавливаем WP

___2. Создаем базу данных

___3. Переходим в админку PHP
По умолчанию ия пользователя root, нет пароля

___4. В админке - создать БД, дать название (как проект чтобы не запутаться, кодировка д.б. utf8_general_ci),

___5. В привилегиях - создаем пользователя (добавить учетную запись),
имя - admin и пароль. Указать права (все).

___6. В WP - записать имя БД, 

___7. Далее заполнять имя сайта и пр. 

___8. Создать файл CSS и для массового исполльзоавния прописать что-от типа:

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

___9. Создаем файл index.php

___10. Загрузить превью в папку под именем screenshot.png

___11. Сделать файл 404.php и оформить его отдельно. Подключается автоматом.

___12. В index.php пишем:
<?php get_header() ?>
<?php get_footer() ?> 
Для подключения соответствуюших файлов.

___13.Создаем файлы
header.php  
footer.php

___14. В файл header.php
залить из index.html код с самого начала до закрывающегося тега </header>

___15. В файл footer.php 
залить из index.html код с начала тэга footer до самого конца кода

___16. В index.php
залить из index.html остальной код 

___17. Перенести в папку проекта все необходимые папки

___18. Создать файл functions.php для определения путей к папкам и прочий функционал

___19. В папке functions.php:

Прописываем команду поиска файлов стилей.
<?php 

	echo get_stylesheet_uri();

В проекте сайта появится абсолютный адрес пути.

___20. Далее в папке functions.php добавляем код (итоговый вид):

<?php

add_action( 'wp_enqueue_scripts', 'my_scripts_method' );
function my_scripts_method(){
	wp_enqueue_script( 'newscript', get_template_directory_uri() . '/js/custom_script.js');
}

при этом уже не нужен 
echo get_stylesheet_uri()
и его можно удалить

___21. После "<?php" и перед "add_action" создаем:
 
define("B_THEME_ROOT", get_template_directory_uri()); - определяем папку стилей. B_THEME_ROOT это константа, 
которую потом можно использовать. Это д.б. уникальное имя. Эти константы можно использовать для других подключений 
типа css и пр. См примеры далее.

___22. Далее - добавляем файлы стилей и иные подключаемые файлы кодом:

define("B_CSS_DIR", B_THEME_ROOT . "/css");
define("B_JS_DIR", B_THEME_ROOT . "/js");
define("B_IMG_DIR", B_THEME_ROOT . "/img");

___23. В add_action вместо 'my_scripts_method' обозначаем свое название.
В function (делее код) также его переименовываем.
К примеру: "up_style"

___24. В function up_style подключаем стили, вводя новый код (вместе с предыдущим он выглядит так).
При этом названия типа  'main' 'media' 'animate' - это все произвольные названия констант. ДАлее - идет директория 
и еще далее - дальнейший путь.

 //add style
   function up_style(){
      wp_enqueue_style( 'bootstrap', B_CSS_DIR . '/bootstrap/bootstrap.min.css');
      wp_enqueue_style( 'main', B_CSS_DIR . '/style.css');
      wp_enqueue_style( 'mediacss', B_CSS_DIR . '/media.css');

        }

___25. Необходимо деактивировать JS Qerry is WP и подключать там же в function, через пробел от предыдущей строчки: 

wp_deregister_script("jquerry");

___26. Далее подключаем все файлы js в functions там же после отключения jquerry.
И далее - подключается свой jquerry, но самым первым:

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

___27. Переходим в header.php и удаляем имеющиеся там подключения.
<!-- Bootstrap -->
	<link rel="stylesheet" href="css/bootstrap/bootstrap.min.css">

	<link rel="stylesheet" href="css/style.css?014">

	<link rel="stylesheet" href="css/media.css?015">


и переподключаем вместо него:
<?php wp_head(); ?>


___28. То же самое подключаем в footer.php перед </body>
<?php wp_footer(); ?>

___29. В header.php пишем вместо адреса img следующий код:
<?php echo B_IMG_DIR ?>/first_screen_bg.jpg" (после / - наш путь)

___30. Регистрируем меню.
В файле functions.php
в любом месте ниже чем уже все написанное...

add_action( 'after_setup_theme', 'theme_register_nav_menu' );
function theme_register_nav_menu() {
register_nav_menu( 'primary', 'Primary Menu' );
}

где
'after_setup_theme' - обязательное событие для привязки,
'theme_register_nav_menu'- то как оно называется для function
function theme_register_nav_menu = после function можно менять название, 
на то, что было выше вместо дэфолтного theme_register_nav_menu.
primary = то как оно называется в коде вообще, типа id или класса.
Primary Menu = то как оно будет называться в консоли 

___31. В консоли далее настроить меню, кнопки и пр. во вкладке редактированния меню, 
там же создаем предварительно это меню.
Во вкладке управление областями выбираем то название меню, к которому это применяется - 
и далее нажать кнопку сохранить
 

___32. После того, как меню зарегистрировано, 
Сначала зайти в header.php и в div где содержится это меню (пред <ul>)
пишется код
<?php wp_nav_menu([
'theme_location'  => '',
]); ?>

где 'theme_location'  => '', 'место, откуда берется меню. 
В functions.php меню будет в top (заданное ранее произвольно название)

После этого в том же массиве ставится 'container'       => 'null', 
для управления блоком и распространения на него стилей css. 
При этом значение может быть разное - см. документацию 

___33. Убирается список ul.
А список li, который имел класс lamb и был связан с JS остается.
Список li нужно отредактиврать по необхожимости, как и прочие элементы, через ИР.


___34. В консоли - стилизовать меню.
Там где необходима якорная ссылка - делать писать в поле адреса # и без пробела - название якорной ссылки
К примерк #about 
Работате через id, котрое указано было в коде


___35. Чтобы сделать второе меню в function.php дублируем код
add_action( 'after_setup_theme', 'mobile_menu' );
function mobile_menu() {
register_nav_menu( 'primary', 'Primary Menu' );
}

В консоли WP надо создать новое меню.

А в header - вставить код 
<?php wp_nav_menu([
'theme_location'  => 'top',
'container'       => null
]); ?>
вместо соответствюущего мобильного списка

___36.
В header заменить:
<html <?php bloginfo( "language" ); ?>>
<head>
<meta charset="<?php bloginfo( "charset" ); ?>">
<title><?php bloginfo( "name" ); ?></title>
<meta name="description" content="<?php bloginfo( "description" ); ?>">

тогда все это будет стилизовться через WP

___37. Плагины WP

1 = All in One SEO Pack
https://ru.wordpress.org/plugins/all-in-one-seo-pack/

2 = Broken Link Checker
https://ru.wordpress.org/plugins/broken-link-checker/

3 = Contact Form 7
https://ru.wordpress.org/plugins/contact-form-7/

4 = Imagify – WebP & Image Compression and Optimization
https://ru.wordpress.org/plugins/imagify/

5 = Jetpack от WordPress.com
https://ru.wordpress.org/plugins/jetpack/

6 = Migrate Guru: Migrate & Clone WordPress Free
https://ru.wordpress.org/plugins/migrate-guru/

7 = WordPress Gallery Plugin — NextGEN Gallery
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
в плагинах WP

___38. Добавленное через Download Monitor меню "загрузки" настроить и добавить новую.
Скопировать название из кода там где непосредственно название этой кнопки, а не тэги.

Далее - добавить соответствующий файл и далее - вставить URL.	
И далее - опубликовать.
Далее использовать шорткод с командой, которую пишем вместо названия кнопки в header.php
echo do_shortcode('[somename]'); 

То есть, вместо 

<p><a href="download/CV.doc" download>Download CV</a></p>

пишем 

<p><a href=""><?php echo do_shortcode('[download id="21"]'); ?></a></p>
где [download id="21"] это скопированный шорткод из консоли WP

если есть лишняя обертка, ее следует убрать.

___39. Динамическое изменение логотипа.
Вместо кода :
<h1 class="logo"><a href="index.html">B.</a></h1>

писать по форме
<h1 class="logo_img"><a class="none" href="">Brendon - Personal HTML Template For Creative Professionals</a></h1>

Далее - в functions.php добавить

add_theme_support( 'custom-logo', [
	'height'      => 190,
	'width'       => 190,
	'flex-width'  => false,
	'flex-height' => false,
	'header-text' => '',
] );

или оставить для того, чтобы не задавать четкие ограничения 

add_theme_support( 'custom-logo');

Во вкладке - "внешний вид", "настроить", "свойства сайта", "логотип"

В header.php там где был код логотипа обернуть кодом:
<?php if(has_custom_logo()) {
the_custom_logo();
} else { ?>
<h1 class="logo_img"><a class="none" href="">Brendon - Personal HTML Template For Creative Professionals</a></h1>
<?php } ?>

где идет проверка на логотип the_custom_logo, который идет из консоли и если его нет, то 
вставляется тот что по ссылке.

___40. Изменение баннеров в консоли

add_theme_support( 'custom-header', array(
         'width'         => 980,
         'height'        => 60,
         'default-image' => get_template_directory_uri() . '/images/header.jpg',
         'uploads'       => true,
      ) );

Если какие-о параметры определены в верстке, их указывать здесь не надо.
К примеру:
add_theme_support( 'custom-header', array(
'default-image' => get_template_directory_uri() . '/images/header.jpg',
'uploads'       => true,
      ) );
 
Если картинка не срабатывает - проверить надичие определения в основной верстке.
(header.php)

и вставить вместо адреса следующий код
<?php header_image(); ?>

___41.Регистрация нового поля. Для двух полей - через код.

___ 41.1

После всех кодов добавить и оставить нужное:

add_action( 'init', 'register_post_types' );
   function register_post_types(){
	   register_post_type('hello', array(
		'labels' => array(
			'name'               => 'Приветствие', // основное название для типа записи
			'singular_name'      => 'Приветствие', // название для одной записи этого типа
			'add_new'            => 'Добавить Приветствие', // для добавления новой записи
			'add_new_item'       => 'Добавление Приветствие', // заголовка у вновь создаваемой записи в админ-панели.
			'edit_item'          => 'Редактирование Приветствие', // для редактирования типа записи
			'new_item'           => 'Новое Приветствие', // текст новой записи
			'view_item'          => 'Смотреть Приветствие', // для просмотра записи этого типа.
			'search_items'       => 'Искать Приветствие', // для поиска по этим типам записи
			'not_found'          => 'Не найдено', // если в результате поиска ничего не было найдено
			'not_found_in_trash' => 'Не найдено в корзине', // если не было найдено в корзине
			'parent_item_colon'  => '', // для родителей (у древовидных типов)
			'menu_name'          => 'Приветствие в баннере', // название меню
		),
		
		'public'              => false,
		'show_ui'             => true,
		'menu_icon'           => "dashicons-editor-contract", 
		'supports'            => array( 'title', 'editor' ), // 
		) );
}


Далее после 

function getHello() {
   
   $posts = get_posts( array(
	'orderby'     => 'date',
	'order'       => 'ASC',
	'post_type'   => 'hello',
) );
   return $hello
}

или более старый вариант

function getHello() {
   
   $args = array(
	'orderby'     => 'date',
	'order'       => 'ASC',
	'post_type'   => 'hello',
);
   return get_posts($args);
}

В header перед 
<div class="content_name">
<p class="hello">WELCOME. I AM</p>
<p class="name">BRENDON WILLIAMS</p>
</div>

необходимо добавить функцию 
<?php foerach (getHello() as $post): ?>

перед тем блоком

и

<?php endforeach; ?>

после

--- получается в header

<?php foreach (getHello() as $post): ?>
<div class="content_name">
<p class="hello">WELCOME. I AM</p>
<p class="name">BRENDON WILLIAMS</p>
</div>
<?php endforeach; ?>	
---

Далее вместо WELCOME. I AM необходимо вставить функцию 
<?php echo $post->post_title;>

где post_title и post_content нужно будет найти через var_dump.

Вместо BRENDON WILLIAMS
вставляется

<?php echo $post->post_content;>

В итоге блок будет выглядеть так

<?php foreach (getHello() as $post): ?>
<div class="content_name">
<p class="hello"><?php echo $post->post_title; ?></p>
<p class="name"><?php echo $post->post_content; ?></p>
</div>
<?php endforeach; ?>	

Для его работы в functions.php следует добавить код:

function getHello() {
   
   $args = array(
	'orderby'     => 'date',
	'order'       => 'ASC',
	'post_type'   => 'hello',
);
   return get_posts($args);
}

42.2 Для большего количества полей можно добавить через плагин.

Плагин - advanced custom felds

В консоли появляется "группы полей"

Далее - добавить

ввести название и тип записи (привтствие и пр.)

Далее - добавить поле, потом заполнить и публиковать.

В графе "приветствие в баннере" появилось новое поле
  

Для включения полей в нужно обновить код в functions php:

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

42.3 в header.php следует отредактировать код
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

то есть вместо переменной $post добавить переменную $bannerTexts

___43. Добавление только через плагин.
добавляем в консоли группу полей и в коде вместо этого поля вводим
<?php the_field("название поля, которое дано в консоли") ?>  

___44. Если не работает счетчки в JS то следует
сделать его начальным скриптом, то есть поместить после кода "use strict";
$(window).on( 'load', function() {

$('.counter').countUp({
	'time': 2000,
	'delay': 10
  });

...___...

___45. Удаление лишнего кода из WP

Использовать функцию remove_action().

в файле function.php
пишется следующий универсальный код 

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

ЕГО НУЖНО ВСТАВЛЯТЬ ПОСЛЕ ОТКРЫВАЩЕГО НАЧАЛЬНОГО ТЭГА PHP в functions.php
  
___46. Добавление галереи WP.

   46.1 Добавить рубрику через консоль. Записи -> Рубрики
   Задать название в поле.

   46.2 Добавить метатеги. Сделать это через консоль в разделе "метки" или они сгенерируются
   сами при публикации новой записи.

   46.3 При наведении на новую рубрику снизу будет высвечиваться путь, где можно посмотреть 	id
рубрики. К примеру I_ID=7&post

   46.4 В index.html удалить имеющуюся разметку portfolio item, оставив одну и добавить цикл.
перед этим item непосредственно в разметке блока.

Вместе с разметкой это выглядит как:

<div class="row">
	<div class="col-md-12 col-sm-12 col-xs-12">
		<div class="isotope_items row">
			<?php if (have_posts()) : query_posts( "cat=номер ID" );
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

размер 360 на 360 определяется по макету.


   46.5 Добавить новую запись через консоль WP -> выбрать созданный для этого раздел (портфолио) -> 
выбрать поле "установить изображение записи" в поле "изображения записи" -> загрузить эти изображения
поодному -> опубликовать каждое.

   46.6 Чтобы при жаталии на картинку грузилась большая картинка необходимо добавить следующий код:
к примеру, вместо 
	<img src="<?php echo B_IMG_DIR ?>/portfolio/work-1.jpg" alt=""> 

добавить:

<img src="<?php $large_image_url = wp_get_attachment_image_src( get_post_thumbnail_id(), "large" );
echo $large_image_url[0]; ?>" alt="">


46.7 Для сортировки картинок по фильтрам необходимо проставлять метки. Они могут быть в коде как фильтры или на самом сайте.
Метки добавляются в разделе с записями, при добавлении нажать на enter.
В коде вместо метки по умолчанию - к приимеру, тут это development

<a href="<?php the_post_thumbnail_url( array(360,360) ); ?>"
class="single_item link development col-md-4 col-sm-6 wow fadeInUp" data-wow-delay="0.3s">

необходимо написать:
<?php $tags = wp_get_post_tags( $post->ID );
if ($tags) {
foreach ($tags as $tag){
echo "" . $tag->name;	
}}?>

то есть, блок в итоге будет такой

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

47. Вставка формы происходит через плагины
Contact Form 7 
и Easy WP SMTP (без которого почта не будет доходить)

В разметке указывается 

	<?php echo do_shortcode( '[contact-form-7 id="50" title="Контактная форма 1"]' ) ?>

где [contact-form-7 id="50" title="Контактная форма 1"] сгенерирован в WP в виде

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

в квадратных скобках сегенированы WP объекты

48. Подключение блога.

В настройках -> чтение, выбрать "На главной странице отображать" - "Ваши последнеи записи".

Далее - создать новую СТРАНИЦУ, дать название и далее - 
появившийся адрес справа скопировать в верстку в Index.php в секцию блога
в кнопку (та, которая ведет на блог), заменив адрес в ней href на тот, который был в WP.

к примеру, http://wpdev/blog/

48.1 Для формирования страницы блога сделать новый файл php, в который перенести разметку
блога из index.

Подключить хэдер и футер сначала и в конце

<?php get_header(); ?>

<?php get_footer(); ?> 

48.2 Чтобы на новой странице отличался хэдер следует сделать новый файл, с обязательным названием header-...php

Перенести разметку из header.php

Перенести соответствующую картинку из разметки статической разметке
К примеру, <header id="home" class="blog_head_bg">.

Заменить часть хэдера на тот, что из страницы - блога в статической разметке.

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
            
вместо
            
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

48.3 При этом в <?php get_header(); ?> следует указать, что выводится именно
новый хэдер.

    <?php get_header('page.php'); ?>
    При этом указывается название не header-page, а просто page, потому что
header содержится в коде перед скобками    

49. Сайдбар.

Необходимо создать новый файл. Sidebar.php
Перенести верстку в файл из соответствующей верстки, вырезав ее.

В page.php добавить код:

<?php get_sidebar(); ?>


49.1 Далее необходимо зарегистрировать sidebar в functions.php через фукнцию
register_sidebar()

Шаблон использования, вставить в functions.php:

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

После регистрации сайдбара WP добавляет в консоли раздел "Виджеты" автоматически.

Чтобы через консоль можно было добавлять виджеты в сайдбар, которые не предусомтрены версткой необходимо использовать функцию dynamic_sidebar(): 

    <?php dynamic_sidebar( $index ); ?>
это код вставить в начало sidebar.php но при этом чтобы он был в разметке, к примеру, в рамках основного дива.

Если сайдбар на сайте один, то  $index можно не указывать. Если несколько, то название нужно указывать, в виде ID такого сайдбара из functions.php

49.3 Для стилизации виджетов, в частности, календаря в functions.php
указывать в коде: 

'before_widget' => '<li id="%1$s" class="widget %2$s">',
задает то как будет оборачиаться виджет из генерируемого кода.
'after_widget'  => "</li>\n",
и после

к примеру:
'before_widget' => '<div class="widget %2$s">',
'after_widget'  => "</div>\n",

Если отступы делаются с помощью дива, то его нужно добавлять в after, к примеру: 
'after_widget'  => '</div><div class="space x-small"></div>',

также: 
'before_title'
если верстка предполагает заданный стиль заголовка, то она переносится из кода.
к примеру:

'before_title'  => '<h5 class="blog-text-uppercase">',

'after_title'   => "</h2>\n",
заменятеся в таком случае на правильный тэг
'after_title'   => "</h5>\n",

49.4
Далее следует стилизовать виджеты по верстке.
При этом легче сделать в коде изначально один класс для виджетов.

2 способа стилизации без правки кода:
- через фильтры в functions.php
- отдельным файлом searchform.php

2й вариант подробнее:

через функцию get_search_form()

Надо:
найти фрагмент из кода, генерируемого WP для searchform по умолчанию, следующего вида:
<form role="search" ' . $aria_label . 'method="get" id="searchform" class="searchform" action="' . esc_url( home_url( '/' ) ) . '">
				<div>
					<label class="screen-reader-text" for="s">' . _x( 'Search for:', 'label' ) . '</label>
					<input type="text" value="' . get_search_query() . '" name="s" id="s" />
					<input type="submit" id="searchsubmit" value="' . esc_attr_x( 'Search', 'submit button' ) . '" />
				</div>
			</form>

и вставить его в searchform.php

Далее заменить в этом коде 
' . 

    на 

<?php

а закрывающиеся 

. '

    на
    
?>    

49.5
Далее адаптировать верстку сайдбара. 
Сравнить имеющуюся верстку из searchform.php и ту что была в sidebar.php и при 
необходимости перенести в searchform.php необходимое.

Можно вставлять и через css при необходимости, к примеру, иконки.

К примеру:

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
Если верстка, генерируемая WP и исходная не соответствуют друг другу можно 
пеернести разметку, название классов из генерируемого WP в style.css. Нужно сравнивать код и там и там и адаптировать.
К примеру, если в верстке есть некий класс, а WP генерирует типа .widget_categories то можно соответствующий класс заменить тем, что генерирует WP.

50. Настройка блога.

50.1 Проверить страницу page.
Найти соответствующий блок. 
Необходим код только 1 записи, остальные будут дублироваться через php.

В итоге блок контента будет выглядеть приблизительно так:

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

											<p>Hello, I’m Brendon, Creative Designer & User Experience Engineer based in New York – I create awesome web digital products. I know you can too.</p>
											<div class="blog-buttons">
												<a href="blog-single.html">read more
													<i class="fa fa-long-arrow-right"></i>
												</a>
											</div>
										</div>
									</div>
								</div>

50.2 Перед этим кодом, но не сначала, а там где будет начинаться запись блога добавить:

<?php if (have_posts()){ while (have_posts()) {the_post(); ?>
(...далее блок с блогом...)

<?php } /*конец while*/?>
<?php } /*конец if*/?>

C примером выше он будет после кода 

<div class="col-md-9">
    <div class=" blog-content">
    
50.3 Если код выше не позволяет делать блог, то можно делать через переменную 
$query, которая позволит делать обращение к базе данных... 

Где:
- WP_Query это переменная из кодекса.

- 'post_per_page' => '4', - это количество блог-записей на странице. Также это можно задавать в консоли - настройки - чтение.

Не следует допускать конфликтов. Если необходимо потом устанавливать количество страниц вручную эту записать можно удалить из кода.

- 'category_not_in' => '7', - говорит, что записи из рубрики под номером айди 7 (или иного айди, который был генерирован WP - см. выше про тот раздел) не выводить в блог так как они будут рушить верстку.

- 'paged' => get_query_var('paged') ?: 1); - необходима для пагинации.




...то его следует сделать в следующем виде с учетом примера

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

											<p>Hello, I’m Brendon, Creative Designer & User Experience Engineer based in New York – I create awesome web digital products. I know you can too.</p>
											<div class="blog-buttons">
												<a href="blog-single.html">read more
													<i class="fa fa-long-arrow-right"></i>
												</a>
											</div>
										</div>
									</div>
								</div>
								<?php } /*конец while*/?>
								<?php } /*конец if*/?>
                                                  
50.4               

Для настройки самого поста следет указать вместо путя a href 
<a class="blog-img" href="blog-single.html">
в верстке блога - код:

<a class="blog-img" href="<?php the_permalink(); ?>">

Вместо картинки 
<img src="img/blog-grid/blog-grid-1.jpg" alt="">
указать код
<?php the_post_thumbnail (); ?>

Размеры изображения уже задавались ранее через ( array(360,360) ) и здесь также это можно сделать. То есть,
<?php the_post_thumbnail ( array(371,278)); ?>

Для выведения оглавления - заменить код с оглавлением на код 
<?php the_title(); ?>

То есть, в итоге: <h4 class="blog-text-uppercase"><?php the_title(); ?></h4>

Для выведения автора - код с автором
<?php the_author(); ?>

Для выведения даты...
<?php echo get_the_date('n-j-Y'); ?>

Для выведения самого поста - заменить разметку на код:

<?php the_content(); ?>

50.5 Пагинация

Обязатльно располагать между этим кодом

<?php } /*конец while*/?>
<?php } /*конец if*/?>

То есть 

<?php } /*конец while*/?>
<?php the_post_pagination(); ?>
<?php } /*конец if*/?>

Такой код сработает на "простых" страницах, но в блоге следует делать:

<?php } /*конец while*/?>
<?php 
    $wp_query = $query;
    the_post_pagination(); ?>
<?php } /*конец if*/?>

Сам код вида следует закомментировать

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


Чтобы блог выводился не полностью, а частично - следует код 
<?php the_content(); ?>
заменить кодом
<?php the_excerpt(); ?>

50.6 Для настройки пагинации:

в код <?php 
    $wp_query = $query;
    the_post_pagination(--в это место--); ?>

    добавить:
$args = array(
	'show_all'     => false, // показаны все страницы участвующие в пагинации
	'end_size'     => 1,     // количество страниц на концах
	'mid_size'     => 1,     // количество страниц вокруг текущей
	'prev_next'    => true,  // выводить ли боковые ссылки "предыдущая/следующая страница".
	'prev_text'    => __('« Previous'),
	'next_text'    => __('Next »'),
	'add_args'     => false, // Массив аргументов (переменных запроса), которые нужно добавить к ссылкам.
	'add_fragment' => '',     // Текст который добавиться ко всем ссылкам.
	'screen_reader_text' => __( 'Posts navigation' ),
);

И настроить что нужно, например

<?php 
    								$wp_query = $query;
									the_posts_pagination(
									$args = array(
                                    'show_all'     => true, // показаны все страницы участвующие в пагинации
									'prev_next'    => true,  // выводить ли боковые ссылки "предыдущая/следующая страница".
									'prev_text'    => 'BACK',
									'next_text'    => 'NEXT'
									
									));
?>

Удаление h2 из пагинации, который генерируется автоматически.

В functions php добавить фильтр 

add_filter('navigation_markup_template', 'my_navigation_template', 10, 2 );
function my_navigation_template( $template, $class ){
	/*
	Вид базового шаблона:
	<nav class="navigation %1$s" role="navigation">
		<h2 class="screen-reader-text">%2$s</h2>
		<div class="nav-links">%3$s</div>
	</nav>
	*/
	
Далее следует привести код из functions.php в тот вид, который был в макете.

<div class="col-md-12">
	<nav class="box-pagination text-center navigation %1$s" role="navigation">
    <div class="nav-links">%3$s</div>
   </nav>
   </div>

При этом, если добавляется новый блок - его добавлять полностью, если к примеру как в nav были класы к макете, но у самого nav был класс "navigation %1$s" то его оставляют. 

	
Если в разметке указано, что пагинация осуществляется через a, а у нас через li, то следует смотерть все элементы функции pagination_links в документации чтобы исправить это.

К примеру, type задает настраиваемый тэг, с помощью которого осуществляется вставка паганиции. То есть, доавляем в page.php

type - list.

<?php 
    								$wp_query = $query;
									the_posts_pagination(
									$args = array(
										'show_all'     => true, // показаны все страницы участвующие в пагинации
										'prev_next'    => true,  // выводить ли боковые ссылки "предыдущая/следующая страница".
										'prev_text'    => 'BACK',
										'next_text'    => 'NEXT'
										'type'         => 'list'
									)); 
									?>

Если в верстке есть класс "active" - его всегда следует менять на "current" с учетом верстки!!!

Чтобы убрать отображение блока портфолио из рубрик следует поправить файл class-wp-widget-categories

Там в коде 	$cat_args = array(
			'orderby'      => 'name',
			'show_count'   => $c,
			'hierarchical' => $h,
		);
		
		добавить 
		
			$cat_args = array(
			'orderby'      => 'name',
			'show_count'   => $c,
			'hierarchical' => $h,
			'exclude' => 'тут указать айди раздела',
		);


Далее - создать файл category.php 
В него перенести разметку блога вместе с футером если он есть. 
При этом ряд кода убирается, который там нужен для того, чтобы работал на другой странице.

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
								<?php } /*конец while*/ ?>
								<?php 
    								the_posts_pagination(
									$args = array(
										'show_all'     => true, // показаны все страницы участвующие в пагинации
										'prev_next'    => true,  // выводить ли боковые ссылки "предыдущая/следующая страница".
										'prev_text'    => 'BACK',
										'next_text'    => 'NEXT',
										'type'         => 'list',
									)); 
									?>
								<?php } /*конец if*/ ?>
							
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

Для подключения поиска создать search.php и скопировать туда код полностью из category.php.

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
								<?php } /*конец while*/ ?>
								<?php 
    								the_posts_pagination(
									$args = array(
										'show_all'     => true, // показаны все страницы участвующие в пагинации
										'prev_next'    => true,  // выводить ли боковые ссылки "предыдущая/следующая страница".
										'prev_text'    => 'BACK',
										'next_text'    => 'NEXT',
										'type'         => 'list',
									)); 
									?>
								<?php } /*конец if*/ ?>
							
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


При этом файл searcform.php следует откорректировать в следующем виде:

<form role="search" method="get" id="searchform"  action="<?php echo home_url( '/' ) ?>">
	<div class="search-form  fullwidth">
	<div class="form-group">
		<input type="text" value="<?php get_search_query() ?>" name="s" id="s" placeholder="Enter keyword" class="form-control" />
		<input class="btn btn-search" type="submit" id="searchsubmit" value="найти" />
	</div>
	</div>
</form>

60. Страницы поста
60.1 Для открытия отдельнйо страницы при нажатии на название блога:
Создается файл. single.php
Из соответствующей верстки копируется разметка.

Футер и хэдер меняется соответствующим кодом.
<?php get_footer(); ?>
<?php get_header() ?>
Если хэдер меняется его можно реализовать как новый (см. выше)

Сайдбар подключается через 
<?php get_sidebar(); ?>

Вместо картинки типа:
    <img src="img/blog-list-1.jpg" alt="">
используется код
    <?php the_post_thumbnail(array(360,360) ) ?>
    Дату через 
    <?php echo get_the_date('j F Y'); ?>
    
    Для выведения количества комментариев следует использовать код:
    
<?php comments_number('пока нет комментариев', '1 комментарий', '% комментариев'); ?>.</p>

Для вывода контента:

    <?php the_content(); ?>
Для записи, которая должна быть в цикле следует его задать.
  <?php if (have_posts()) {while(have_posts()) {the_post(); ?>
  .........
  
    <?php } ?>
    <?php } ?>

60.2
Комментарии.
Необходимо создать файл comment.php

В блоке "comments" в файле single.php прописать код вместо верстки 
  <?php if(comment_open()) || get_comments_number()) {
                                    comments_template();
                                } ?>
В comment.php прописать шаблонный готовый код:


<?php if (comments_open()) { ?>
  <h3 class="comments-caption"><a name="comments"><?php comments_number('Комментарии', '1 комментарий', '% комментариев'); ?> читателей статьи "<?php the_title();?>"</a></h3>
    <?php if (get_comments_number() == 0) { ?>
      <ul class="list">
        <li>Оставьте первый комментарий - автор старался</li>
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
                <?php printf(__('@<cite class="fn">%s</cite> <span class="says">пишет:</span>'), get_comment_author_link()) ?>
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
          'reply_text' => 'Ответить',
          'callback' => 'verstaka_comment'
        );
        wp_list_comments($args);
      ?>
    </ol>
  <?php } ?>

  <?php
    $fields = array(
      'author' => '<p class="comment-form-author"><label for="author">' . __( 'Name' ) . ($req ? '<span class="required">*</span>' : '') . '</label><input type="text" id="author" name="author" class="author" value="' . esc_attr($commenter['comment_author']) . '" placeholder="" pattern="[A-Za-zА-Яа-я]{3,}" maxlength="30" autocomplete="on" tabindex="1" required' . $aria_req . '></p>',
      'email' => '<p class="comment-form-email"><label for="email">' . __( 'Email') . ($req ? '<span class="required">*</span>' : '') . '</label><input type="email" id="email" name="email" class="email" value="' . esc_attr($commenter['comment_author_email']) . '" placeholder="example@example.com" maxlength="30" autocomplete="on" tabindex="2" required' . $aria_req . '></p>',
      'url' => '<p class="comment-form-url"><label for="url">' . __( 'Website' ) . '</label><input type="url" id="url" name="url" class="site" value="' . esc_attr($commenter['comment_author_url']) . '" placeholder="www.example.com" maxlength="30" tabindex="3" autocomplete="on"></p>'
    );

    $args = array(
      'comment_notes_after' => '',
      'comment_field' => '<p class="comment-form-comment"><label for="comment">' . _x( 'Comment', 'noun' ) . '</label><textarea id="comment" name="comment" class="comment-form" cols="45" rows="8" aria-required="true" placeholder="Текст сообщения..."></textarea></p>',
      'label_submit' => 'Отправить',
      'fields' => apply_filters('comment_form_default_fields', $fields)
    );
    comment_form($args);
  ?>
  <?php } else { ?>
  <h3>Обсуждения закрыты для данной страницы</h3>
  <?php }
?>

Сравнить с версткой и сделать "слияние" с ней/

К примеру, вместо h3 - вставить  
<h4><?php comments_number('No Comments', '1 comment', '% comments'); ?> comments</h4>

Комментарии обычно в тэге <ol>

Часть разметки - блок из шаблона можно стилизовать самостоятельно, удалив этот:

<div class="comment-author vcard">
                    <div class="comment-meta commentmetadata" style="float: right;">
                    <span><?php printf(__('%1$s at %2$s'), get_comment_date(),  get_comment_time()) ?></span>
                    </div>
                    <?php echo get_avatar($comment,$size='74',$default='<path_to_url>' ); ?>
                    <?php printf(__('@<cite class="fn">%s</cite> <span class="says">пишет:</span>'), get_comment_author_link()) ?>
                </div>
                <?php if ($comment->comment_approved == '0') : ?>
                    <em><?php _e('Your comment is awaiting moderation.') ?></em>
                    <br>
                <?php endif; ?>
                <?php comment_text() ?>
                <div class="reply">
                    <?php comment_reply_link(array_merge( $args, array('depth' => $depth, 'max_depth' => $args['max_depth']))) ?>
                </div>
                
Запись с аватаром можно подключить кодом

<?php echo get_avatar($comment,$size=74,$default='<path_to_url>' ); ?>

Стилизованный он такой к примеру
<?php echo get_avatar($comment,64,'',array('class'=> 'media-object') ); ?>

Для получения имени пользователя, оставившего комментарий через get_comment_author_link() :

echo get_comment_author_link( $comment_ID );    

Для текста комментария используется код: 

<?php comment_text();?>

Для даты использовать код:

<?php echo get_the_date('n-j-Y'); ?>


Далее стилизовать форму обратной связи как надо.
Через comment_form.

Стилизовать можно также через файл wp-include -> comment-template.php

60.3 
Для добавления кнопки Reply следует добавить функцию 
comment_reply_link();

код:
<?php comment_reply_link(array_merge( $args, array('depth' => $depth, 'max_depth' => $args['max_depth']))) ?>

60.4
Для проверки, если комментарий уже опубликован, но ждет модерации, можно исползовать код:

<?php if ($comment->comment_approved == '0') : ?>
    <em><?php _e('Your comment is awaiting moderation.') ?></em>
<br>

после кода 

<h5 class="media-heading blog-text-uppercase"><?php echo get_comment_author_link(); ?></h5>

61. Вывод сообщений на главную страницу сайта.

Следует использовать код 

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
					'suppress_filters' => true, // подавление работы фильтров изменения SQL запроса
				) );
				
				foreach( $posts as $post ){
					setup_postdata($post);
					// формат вывода the_title() ...
				}
				wp_reset_postdata(); // сброс

?>	

При этом начало кода 
$posts = get_posts( array(
перестало работать, поэтому следует использовать код:

62. SEO оптимизация
62.1 Первичная настройка SEO
--Обратить внимание на title, description, h1-h6;
--Страница 404;
--Отсутствие дублированных страниц;
--Скорость загрузки сайта;
--Вес страницы сайта;
--Сжатие js, css и картинок.

Можно использовать плагин Yoast SEO для дальнешей работы SEO-специалиста

Определить стартегии загрузки шрифтов

Для кэширования использовать плагины
W3 total cache и  WP super Cache

63. Защита сайта от взлома.
- Реже использовать плагины;
- Включить автоматическое обновление WP;
- Использовать код remove_wp_version_strings;
- Перенести адрес страницы логина;
- Изменить логни по умолчанию;
- Использовать плагины безопасности;
- Удалить лишние файлы. "readme .html" \ "install.php";
- В файл wp-config-php периодически менять ключи безопасности;
- В файле .htacess запретить доступ к ряду важных файлов и отключить нумерацию пользователей;
