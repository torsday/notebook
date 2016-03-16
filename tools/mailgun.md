# Mailgun

> Email Service For Developers

---

## Examples

### curl

```sh
curl -s --user 'api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0' \
    https://api.mailgun.net/v3/samples.mailgun.org/messages \
    -F from='Excited User <excited@samples.mailgun.org>' \
    -F to='devs@mailgun.net' \
    -F subject='Hello' \
    -F text='Testing some Mailgun awesomeness!'
```

### Ruby

```ruby
def send_simple_message
  RestClient.post "https://api:key-3ax6xnjp29jd6fds4gc373sgvjxteol0"\
  "@api.mailgun.net/v3/samples.mailgun.org/messages",
  :from => "Excited User <excited@samples.mailgun.org>",
  :to => "devs@mailgun.net",
  :subject => "Hello",
  :text => "Testing some Mailgun awesomeness!"
end
```

### PHP

```php
# Include the Autoloader (see "Libraries" for install instructions)
require 'vendor/autoload.php';
use Mailgun\Mailgun;

# Instantiate the client.
$mgClient = new Mailgun('key-3ax6xnjp29jd6fds4gc373sgvjxteol0');
$domain = "samples.mailgun.org";

# Make the call to the client.
$result = $mgClient->sendMessage("$domain",
  array('from'    => 'Excited User <excited@samples.mailgun.org>',
        'to'      => 'Mailgun Devs <devs@mailgun.net>',
        'subject' => 'Hello',
        'text'    => 'Testing some Mailgun awesomeness!'));
```
---

## References

-   [Mailgun.com](https://www.mailgun.com)
