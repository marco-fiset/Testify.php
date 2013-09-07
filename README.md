Testify - a micro unit testing framework
========================================
Testify makes writing unit tests fun again. It has an elegant syntax and keeps things simple.


Requirements
------------
* PHP 5.3+ is required
* [Composer](http://getcomposer.org/) to install Testify is recommended (but you can do this manually)


Usage
-----
Here is an example for a test suite with two test cases:

```php
require 'vendor/autoload.php';

use Math\MyCalc;
use Testify\Testify;

$tf = new Testify("MyCalc Test Suite");

$tf->beforeEach(function($tf){
	$tf->data->calc = new MyCalc(10);
});

$tf->test("Testing the add() method", function($tf){
	$calc = $tf->data->calc;

	$calc->add(4);
	$tf->assert($calc->result() == 14);

	$calc->add(-5);
	$tf->assertEqual($calc->result(),9);
});

$tf->test("Testing the mul() method", function($tf){
	$calc = $tf->data->calc;

	$calc->mul(1.5);
	$tf->assertEqual($calc->result(),15);

	$calc->mul(-1);
	$tf->assertEqual($calc->result(),-15);
});

$tf();
```

For full documentation and a getting started guide, visit the [Testify homepage](http://tutorialzine.com/projects/testify/).
