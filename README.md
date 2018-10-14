# Wrapper for API [stopforumspam.com](https://www.stopforumspam.com/usage)

[![Build Status](https://secure.travis-ci.org/Gemorroj/StopSpam.png?branch=master)](https://travis-ci.org/Gemorroj/StopSpam)


### Requirements:

- PHP >= 5.6
- ext-curl


### Installation:
```bash
composer require gemorroj/stop-spam
```


### Example check IP:

```php
<?php
use StopSpam\Request;
use StopSpam\Query;

$query = new Query();
$query->addIp('1.2.3.4');

$request = new Request();
$response = $request->send($query);
$item = $response->getFlowingIp();
var_dump($item->isAppears()); // bool (true)
```

##### Async example
```php
<?php
use StopSpam\Request;
use StopSpam\Query;
use StopSpam\Response;

$query = new Query();
$query->addIp('1.2.3.4');

$request = new Request();
$request->sendAsync($query, function (Response $response) {
    $item = $response->getFlowingIp();
    var_dump($item->isAppears()); // bool (true)
});
```
