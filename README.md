
# Simple Template Library for Codeigniter

The simplest template libary for Codeigniter ever. The code is easy to understand and modify it for your needs.

#####Check out Wiki for detailed examples#####

--------------------------

### Installation

Download `Layout.php` to your `application/libraries/` folder.

```php
$this->load->library('Layout');
```
Put **CI_head()** inside **&lt;head&gt;** and **&lt;/head&gt;** tag in view.

Put **CI_footer()** before **&lt;/body&gt;** tag in view.

Put **CI_title()** inside **&lt;title&gt;** and **&lt;/title&gt;** tag in view.

Put **CI_body_attr()** into **&lt;body&gt;** to control attrbutes such as "id", "class" and more.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title><?= CI_title() ?></title>
    <?= CI_head() ?>
</head>
<body<?= CI_body_attr() ?>> 
```

```html
<?= CI_footer() ?>
</body>
</html>
```

All HTML output are handled by CI_head() , CI_footer(), CI_body_attr() and CI_title()


### API Examples
Use the following APIs in controller.


####add_meta

Parameters
```php
/*
 * add_meta (string $name, string $value, string $type = 'meta')
 * @param string $name
 * @param string $value
 * @param string $type - 'meta' or 'link'. Default: 'meta'
 */
```
Example
```php
$this->layout->add_meta('author', 'Terry Lin');
```
Output
```html
<meta name="author" content="Terry Lin" />
```

####add_custom_meta

Parameters
```php
/*
 * add_custom_meta(string $type, array $attributes)
 * @param string $type 
 * @param string array $attributes
 */
```
Example
```php
$this->layout->add_custom_meta('link', array(
    'href' => 'test.php',
    'rel' => 'parent',
    'rev' => 'subsection',
    'hreflang' => 'en'
));
```
Output
```html
<link href="test.php" rel="parent" rev="subsection" hreflang="en">
```
Build special meta tags:
```php
$this->layout->add_custom_meta('meta', array(
    'charset' => 'utf-8'
));
$this->layout->add_custom_meta('meta', array(
    'http-equiv' => 'X-UA-Compatible',
    'content' => 'IE=edge'
));
```
Output
```html
<meta charset="utf-8">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

####add_css_file

Parameters
```php
/*
 * add_css_file ( string $tag_css, string $path = '' )
 * @param string $tag_css
 * @param string $path - $path can be ignored if you set $tag_css as a remote file with full URL, or a local file with absolute path.
 */
```
Example
```php
$this->layout->add_css_file('https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css');
```
Output
```html
<link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet" />
```

####add_css_files

Parameters
```php
/*
 * add_css_files ( array $tag_css, string $path = '')
 * @param array $tag_css
 * @param string $path - $path can be ignored if you set $tag_css as remote files with full URL, or local files with absolute path.
 */
```
Example
```php
$this->layout->add_css_files(array('bootstrap.min.css','style.css'), base_url().'assets/css/');
```
Output
```html
<link href="http://dictpedia.org/assets/css/bootstrap.min.css" rel="stylesheet" />
<link href="http://dictpedia.org/assets/css/style.css" rel="stylesheet" />
```

####add_css_rawtext

Parameter
```php
/*
 * add_css_rawtext ( string $content )
 * @param string $content
 */
```
Example
```php
$css_text = <<<EOF

.text {
	font-size: 12px;
	background-color: #eeeeee;
}
EOF;

$this->layout->add_css_rawtext($css_text);
```
Output
```html
<style>


.text {
	font-size: 12px;
	background-color: #eeeeee;
}

</style>
```

####add_js_file

Parameters
```php
/*
 * add_js_file ( string $tag_js , string $path = '', string $position = 'header' )
 * @param string $tag_js 
 * @param string $path - $path can be ignored if you set $tag_js as a remote file with full URL, or a local file with absolute path.
 * @param string $position - 'header' or 'footer'
 */
```
Example
```php
$this->layout->add_js_file('https://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js');
```
Output
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>
```

####add_js_files

Parameters
```php
/*
 * add_js_files ( array $tag_js , string $path = '', string $position = 'header' )
 * @param array $tag_js 
 * @param string $path - $path can be ignored if you set $tag_js as remote files with full URL, or local files with absolute path.
 * @param string $position - 'header' or 'footer'. Default: 'header'.
 */
```
Example
```php
$this->layout->add_js_files(array('bootstrap.min.js','script'), base_url().'assets/js/');
```
Output
```html
<script src="http://dictpedia.org/assets/js/bootstrap.min.js"></script>
<script src="http://dictpedia.org/assets/js/script.js"></script>
```

####add_js_rawtext

Parameters
```php
/*
 * add_js_rawtext ( string $content , string $position = 'header')
 * @param string $content
 * @param string $position - 'header' or 'footer'. Default: 'header'.
 */
 ```
Example
```php
$js_text = <<<EOF
alert('this is just a test');
EOF;

$this->layout->add_js_rawtext($js_text, 'header');
```
Output
```html
<script>

alert('this is just a test');

</script>
```

####set_title

Parameter
```php
/*
 * set_title ( string $title )
 * @param string $title
 */
 ```
Example
```php
$this->layout->set_title('Test! This is a test title');
```
Output
```html
<title>Test! This is a test title</title>
```
####set_body_attr

Parameter
```php
/*
 * set_body_attr ( array $attribute )
 * @param array $attribute
 */
 ```
Example
```php
$this->layout->set_body_attr(array('id' => 'home', 'class' => 'global white-bg'));
```
Output
```html
<body id="home" class="global white-bg">
```

####get_title
alias => CI_title()
```php
$this->layout->get_title();
```

####get_body_attr
alias => CI_body_attr()
```php
$this->layout->get_body_attr();
```

####get_header
alias => CI_head()
```php
$this->layout->get_header();
```

####get_footer
alias => CI_footer()
```php
$this->layout->get_footer();
```


### Built-in Meta Tags

#### $meta_default
author, viewport, keywords, description, canonical

```php
// examples
$this->layout->meta_default['author'] = 'Terry Lin';
$this->layout->meta_default['description'] = 'This is just a test file';
```

#### $meta_twitter
url, site, creator, card, title, description, image_src

```php
// examples
$this->layout->meta_twitter['card'] = 'summary_large_image';
$this->layout->meta_twitter['image_src'] = 'http://test.test/test.gif';
```

#### $meta_facebook
site_name, url, title, type, description, image, admins, app_id

```php
// examples
$this->layout->meta_facebook['site_name'] = 'Demo Site';
$this->layout->meta_facebook['description'] = 'This is just a test file';
$this->layout->meta_facebook['app_id'] = '1123123152';
```
