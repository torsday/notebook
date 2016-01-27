# Model

## e.g. ```EmailChange.php```

*reach-php/src/CPT/Reach/Domain/Model/User/EmailChange.php*

```php
namespace Reach\Domain\Model\User;

use Common\Domain\Model\DateTime;
use Common\Domain\Model\Event;
use Reach\Domain\Model\BaseUser;

/**
 * Represents an Email Change Event of a User in the domain.
 */
class EmailChange implements Event
{
    /**
     * @var Email
     */
    protected $email;
    /**
     * @var DateTime
     */
    protected $when;
    /**
     * @var BaseUser
     */
    protected $author;

    /**
     * EmailChange constructor.
     *
     * @param Email    $email
     * @param DateTime $when
     * @param BaseUser $author
     */
    public function __construct(
        Email    $email,
        DateTime $when,
        BaseUser $author
    ) {
        $this->email = $email;
        $this->when  = $when;
        $this->author = $author;
    }

    /**
     * Returns the Date and Time when the email changed.
     *
     * @return DateTime
     */
    public function when()
    {
        return $this->when;
    }

    /**
     * Returns the email.
     *
     * @return Email
     */
    public function getEmail()
    {
        return $this->email;
    }

    /**
     * Returns the user responsible for the change.
     *
     * @return BaseUser
     */
    public function getAuthor()
    {
        return $this->author;
    }
}
```
