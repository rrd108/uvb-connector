# UV-B API Connector

This package is the PHP connector for the UV-B API 1.0.

## Installing

The easiest way to install the Connector is using Composer:

```
composer require webmenedzser/uvb-connector
```

Then use your framework's autoload, or simply add:

```php
<?php
  require 'vendor/autoload.php';
```

## Manual install

If you wish to omit using Composer altogether, you can download the sources from the repository and use any [PSR-4](http://www.php-fig.org/psr/psr-4/) compatible autoloader.

## Getting started

You can start making requests to the UV-B API just by creating a new `Request` instance

```php
<?php
  use webmenedzser\UVBConnector\UVBConnector;

  $email = 'tim@apple.com';
  $publicApiKey = 'aaaa';
  $privateApiKey = 'bbbb';

  $connector = new UVBConnector(
    $email, 
    $publicApiKey, 
    $privateApiKey
  );
```

The `UVBConnector` class takes care of the communication between your app and the UV-B API server.

## General usage

### Get e-mail reputation from UV-B API

```php
<?php 
  use webmenedzser\UVBConnector\UVBConnector;

  $email = 'tim@apple.com';
  $publicApiKey = 'aaaa';
  $privateApiKey = 'bbbb';

  $connector = new UVBConnector(
    $email, 
    $publicApiKey, 
    $privateApiKey
  );

  // Get reputation by hash
  $response = $connector->get();
```

### Submit order outcome to UV-B API

```php
<?php
  use webmenedzser\UVBConnector\UVBConnector;

  $email = 'tim@apple.com';
  $publicApiKey = 'aaaa';
  $privateApiKey = 'bbbb';
  // 1 if good, -1 if bad;
  $outcome = 1;

  $connector = new UVBConnector(
    $email, 
    $publicApiKey, 
    $privateApiKey
  );

  // Submit order outcome to API
  $response = $connector->post($outcome);
```