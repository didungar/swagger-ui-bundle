# Swagger UI Bundle

Expose swagger-ui inside your symfony project through a route (eg. /docs), just like [nelmio api docs](https://github.com/nelmio/NelmioApiDocBundle), without the need for node.

Just add a reference to your swagger Yaml or JSON specification, and enjoy swagger-ui in all it's glory.

After installation and configuration, just start your local webserver, and navigate to [/docs](http://127.0.0.1:8000/docs) or [/docs/my_swagger_spec.yml](http://127.0.0.1:8000/docs/my_swagger_spec.yml).

## Installation

Install with composer:

`$ composer require harmbandstra/swagger-ui-bundle`

Enable bundle in `app/AppKernel.php`:

```php
<?php

use Symfony\Component\HttpKernel\Kernel;
use Symfony\Component\Config\Loader\LoaderInterface;

class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = [
            ...
            new HarmBandstra\SwaggerUiBundle\HBSwaggerUiBundle(),
```

Add the route where swagger-ui will be available in `routing.yml`:

```yml
hb_swagger_ui:
    resource: '@HBSwaggerUiBundle/Resources/config/routing.yml'
    prefix: /docs
```

## Configuration

In your `config.yml`, link to the swagger spec.

Specify the `directory` where your swagger files reside. You can access multiple files through the endpoint like `/docs/my_swagger_spec.json`.
Under `files` you specify which files should be exposed. The first file in the array will be the file the `/docs` endpoint will redirect to.

```yaml
hb_swagger_ui:
  directory: "%kernel.root_dir%/../docs/"
  files:
    - "my_swagger_spec.yml"
    - "my_other_swagger_spec.json"
```
