---
layout: post
title: Symfony Get started | Ellioh Thot'o
header-title: Symfony Get started
published: true

tags: 
- Symfony2 
- PHP
---


Installation
-----------

Environment:
Ubuntu

###- Composer : Manage PHP dependencies###
{% highlight bash %}
curl -s https://getcomposer.org/installer | php
{% endhighlight %}


###- Get Symfony sources### 
{% highlight bash %}
composer.phar create-project symfony/framework-standard-edition path/to/install 2.1.x-dev
cd sf-test
rm -rf .git
{% endhighlight %}

###- Test installation### 
Go to the UI configuration testing page 
{% highlight bash %}
http://localhost/sf-test/web/config.php
{% endhighlight %}

Check test result and then :

###- Set rules### 
Go to the UI configuration testing page 
{% highlight bash %}
sudo chown www-data:www-data app/cache/ -R
sudo chown www-data:www-data app/logs/ -R

# take the dir but I can write it too!
sudo chmod 770 app/cache/
sudo chmod 770 app/logs/
sudo adduser elron www-data
{% endhighlight %}

###- Configure apache php.ini### 
{% highlight bash %}
sudo vi /etc/php5/apache2/php.ini
{% endhighlight %}

Set date.timezone to "Europe/Paris"	
Save 
Restart apache 
{% highlight bash %}
sudo service apache2 restart
{% endhighlight %}

Then follow the step of the UI configuration (database, etc.).
At the end of the configuration copy the configuration into "app/config/parameters.yml".

Now enjoy the welcome page :

[http://localhost/sf-test/web/app_dev.php/](http://localhost/sf-test/web/app_dev.php/)


Overview
-------

###The routing### 
Syntax for routing configuration :

{% highlight bash %}
  # app/config/routing_dev.yml
_welcome:
    pattern:  /
    defaults: { _controller: AcmeDemoBundle:Welcome:index }
{% endhighlight %}

When the user request the webservice root (/), Sf will perform :
- Bundle: AcmeDemoBundle
- Controller: Welcome
- Action: index

The following syntax can be used too for _controller value : <code>Acme\DemoBundle\Controller\WelcomeController::indexAction</code>

Routing can be defined in PHP annotation as below :

{% highlight bash %}
// src/Acme/DemoBundle/Controller/DemoController.php
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Template;

class DemoController extends Controller
{
    /**
     * @Route("/hello/{name}", name="_demo_hello")
     * @Template()
     */
    public function helloAction($name)
    {
        return array('name' => $name);
    }

    // ...
}
{% endhighlight %}


###The controllers###
Controller sample : 
{% highlight bash %}
// src/Acme/DemoBundle/Controller/WelcomeController.php
namespace Acme\DemoBundle\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\Controller;

class WelcomeController extends Controller
{
    public function indexAction()
    {
        return $this->render('AcmeDemoBundle:Welcome:index.html.twig');
    }
}
{% highlight bash %}

<code>render</code> function load view template. Here it is a "twig" template. Twig is a template engine.

Template can be automatically render by using by using the annotation <code>@Template()</code> as below :

{% highlight bash %}
// src/Acme/DemoBundle/Controller/DemoController.php
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Route;
use Sensio\Bundle\FrameworkExtraBundle\Configuration\Template;


class DemoController extends Controller
{
    /**
     * @Route("/hello/{name}", name="_demo_hello")
     * @Template()
     */
    public function helloAction($name)
    {
        return array('name' => $name);
    }

    // ...
}
{% endhighlight %}

For me one of the must sweet tool in symfony development is the so userfriendly sf debug bar. 


![toolbar picture 1](http://symfony.com/doc/current/_images/web_debug_toolbar.png)

![toolbar picture 2](http://symfony.com/doc/current/_images/profiler.png)

References and learn more
-------

- [http://symfony.com/doc/current/quick_tour/the_big_picture.html](http://symfony.com/doc/current/quick_tour/the_big_picture.html)
- [https://github.com/composer/composer](https://github.com/composer/composer)
- [http://twig.sensiolabs.org/](http://twig.sensiolabs.org/)


Ellioh Thot'o
