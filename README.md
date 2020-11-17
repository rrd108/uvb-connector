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

You can start making requests to the UV-B API just by creating a new `UVBConnector` instance and calling it's `get()` or `post($outcome)` method. 

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
  
  // Set a threshold for the request
  $connector->threshold = $threshold;

  // Get reputation by hash
  $response = $connector->get();
```

The API will answer with a JSON string with a structure like this: 

```json
{
    "status": 200,
    "message": {
        "good": 3,
        "bad": 5,
        "goodRate": 0.375,
        "badRate": 0.625,
        "totalRate": -0.25,
    }
}
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
