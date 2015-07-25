Forked and updated for v3 from: https://github.com/drewm/mailchimp-api

MailChimp API
=============

Super-simple, minimum abstraction MailChimp API v3 wrapper, in PHP.

I hate complex wrappers. This lets you get from the MailChimp API docs to the code as directly as possible.

Requires PHP 5.3 and a pulse. Abstraction is for chimps.

Installation
------------

You can install the mailchimp-api using Composer:

```
composer require drewm/mailchimp-api
```

You will then need to:
* run ``composer install`` to get these dependencies added to your vendor directory
* add the autoloader to your application with this line: ``require("vendor/autoload.php")``

Alternatively you can just download the MailChimp.php file and include it manually.

Examples
--------

List lists (lists/list method)

	<?php
	$MailChimp = new \Drewm\MailChimp('abc123abc123abc123abc123abc123-us1');
	print_r($MailChimp->call('lists/list'));

Init (updated)

	<?php
	$MailChimp = new \Drewm\MailChimp('abc123abc123abc123abc123abc123-us1');

Get subscribers (updated)
	
	<?php
	$result = $MailChimp->call('lists/{listID}/members', 'GET');
	print_r($result);

Subscribe someone to a list (updated)

	<?php
	$result = $MailChimp->call('lists/{listID}/members', 'POST', array(
					'id'                => 'listID',
					'status'            => 'subscribed',
					'email_address'     => 'davy@example.co,
					'merge_fields'      => array('FNAME'=>'Davy', 'LNAME'=>'Jones'),
					'double_optin'      => false, // doesn't seem necessary in v3
					'update_existing'   => true, // doesn't seem necessary in v3
					'replace_interests' => false, // doesn't seem necessary in v3
					'send_welcome'      => false, // doesn't seem necessary in v3
				));
	print_r($result);


*Note for contributors:* This is not Code Golf.
