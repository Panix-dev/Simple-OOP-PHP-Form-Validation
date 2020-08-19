# Simple OOP PHP Form Validation

> A simple form validation using PHP in an OOP way.

Everything is much cleaner and well structured when you try to code in a more object-oriented way. This is a simple form that uses a PHP Class to validate the fields.


## Table of Contents


> Try `clicking` on each of the `anchor links` below so you can get redirected to the appropriate section.


- [Constructor](#laravel-livewire)
- [validateForm](#validateform)
- [validateUsername](#validateusername)
- [validateEmail](#validateemail)
- [Calling the Class](#calling-the-class)
- [Contact Details](#contact-details)
- [Inspiration](#inspiration)


## Constructor


```php
private $data;
private $errors = [];
private static $fields = ['username', 'email'];

public function __construct($post_data) {
	$this->data = $post_data;
}
```


## validateForm


```php
public function validateForm() {
	foreach(self::$fields as $field){
		if(!array_key_exists($field, $this->data)){
			trigger_error("'$field' is not present in the data");
			return;
		}
	}
	$this->validateUsername();
	$this->validateEmail();

	return $this->errors;
}
```


## validateUsername


```php
private function validateUsername(){
	$val = trim($this->data['username']);

	if(empty($val)){
		$this->addError('username', 'username cannot be empty');
	} else {
		if(!preg_match('/^[a-zA-Z0-9]{6,12}$/', $val)){
			$this->addError('username','username must be 6-12 chars & alphanumeric');
		}
	}

}
```


## validateEmail


```php
private function validateEmail(){
	$val = trim($this->data['email']);

	if(empty($val)){
	 	$this->addError('email', 'email cannot be empty');
	} else {
		if(!filter_var($val, FILTER_VALIDATE_EMAIL)){
			$this->addError('email', 'email must be a valid email address');
		}
	}

}
```


## Calling the Class


```php
if(isset($_POST['submit'])) {
	// Validate the entries
	$validation = new UserValidator($_POST);
	$errors = $validation->validateForm();
}
```


## Contact Details


> :computer: [https://pagapiou.com](https://pagapiou.com)

> :email: [hello@pagapiou.com](mailto:hello@pagapiou.com)

> :iphone: [LinkedIn](https://www.linkedin.com/in/agapiou/)

> :iphone: [Instagram](https://www.instagram.com/panos_agapiou/)

> :iphone: [Facebook](https://www.facebook.com/panagiotis.agapiou)

