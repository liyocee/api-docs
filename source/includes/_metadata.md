# Metadata

> Example showing how to create a new payment with Metadata:

```shell
curl https://app.beyonic.com/api/payments -H "Authorization: Token ab594c14986612f6167a975e1c369e71edab6900" \
-d phonenumber=+256772781923 \
-d currency=UGX \
-d amount=30 \
-d description="Per diem payment" \
-d callback_url="https://my.website/payments/callback" \
-d metadata.id=1234 \ 
-d metadata.name=Lucy \
-d payment_type=money
```

```ruby
require 'beyonic'
Beyonic.api_key = 'ab594c14986612f6167a975e1c369e71edab6900'

payment = Beyonic::Payment.create(
    phonenumber: "+256773712831",
    amount: "100.2",
    currency: "UGX",
    description: "Per diem payment",
    payment_type: "money",
    callback_url: "https://my.website/payments/callback",
    'metadata.id'=> 1234,
    'metadata.name'=> 'Lucy'
)
```

```php
<?php
require_once('./lib/Beyonic.php');
Beyonic::setApiKey("ab594c14986612f6167a975e1c369e71edab6900");

Beyonic_Payment::create(array(
  "phonenumber" => "+256773712831",
  "amount" => "100.2",
  "currency" => "UGX",
  "description" => "Per diem payment",
  "payment_type" => "money",
  "callback_url" => "https://my.website/payments/callback",
  "metadata.id" => "1234", 
  "metadata.name" => "Lucy"
));
?>
```

```python
import beyonic
beyonic.api_key = 'ab594c14986612f6167a975e1c369e71edab6900'

kwargs = {'metadata.id': 1234, 'metadata.name': 'Lucy'}

beyonic.Payment.create(phonenumber='+256773712831',
                       amount='1200', 
                       currency='UGX',
                       description='Per diem',
                       callback_url='https://my.website/payments/callback',
                       **kwargs
                       )
```

Beyonic supports Metadata, which allows you to add custom key-value attributes when creating objects. For example, you can include a unique ID to identify a payment, or add more information about a Contact. This data will be returned when you retrieve the record later, and can be used to identify the record.

Metadata has the following constraints:

* Metadata attributes must be key-value pairs. 
* Both the keys and values must be strings.
* For each record, you can have up to 10 custom attributes.

Metadata is added to the object a set of key-value pairs, where the key is in the format metadata.key_name, for example: metadata.id or metadata.name or metadata.date, and so on.

See the examples for more information.