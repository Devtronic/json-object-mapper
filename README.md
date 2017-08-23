# JOM - JSON Object Mapper

JOM is a powerful object mapper which maps JSON Data into PHP objects.

## Installation
You can install this library using composer

```bash
$ composer require mintware-de/json-object-mapper
```

## Usage
JOM is totally easy to use. 
Simply put the annotation @MintWare\JOM\JsonField(name=, type=) to your class properties.
**name** is the name of the json property, **type** is the field type which can also be an mapped class.

For mapping you have to create an ObjectMapper-Object and call the mapJson Method

## Example
Dataset:
```json
{
    "first_name": "Pete",
    "surname": "Peterson",
    "age": 28,
    "address": {
        "street": "Mainstreet 22a",
        "zip_code": "A-12345",
        "town": "Best Town"
    }
}
```

Data Class:
```php
<?php

use MintWare\JOM\JsonField;

class Person
{
    /** @JsonField(name="first_name", type="string") */
    public $firstName;
    
    /** @JsonField(name="surname", type="string") */
    public $lastname;
    
    /** @JsonField(name="age", type="int") */
    public $age;
    
    /** @JsonField(name="address", type="Some\Other\DataClass\Address") */
    public $address;
}
```

Map the JSON:
```php
<?php

use  MintWare\JOM\ObjectMapper;

$mapper = new ObjectMapper();
$person = $mapper->mapJson(file_get_contents('person.json'), Person::class);
```

## Testing
```bash
$ phpunit
```

## Contribute
Feel free to fork, contribute and create pull requests