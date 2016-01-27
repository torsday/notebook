# Service

A Service in Domain Driven Design is simply a stateless object that performs an action.

## Types of Service

1. **Application Service** is typically used to orchestrate how the outside world interacts with your application. For example ```AuthenticationService``` would be an Application Service that co-ordinates how a user should be authenticated.
1. **Infrastructure Service** is used for dealing with the technical details of the infrastructure. For example you might have a ```MailGunMessenger``` service that enables you to send email notifications using the MailGun API.
1. **Domain Service** is used for encapsulating domain logic that does not naturally fit on any existing Domain Object. For example you might have a ```RegisterUserService``` that co-ordinates how a user is registered within your application.

## e.g. ```EmailHistoryService.php```

*reach-php/src/CPT/Reach/Application/Service/User/EmailHistoryService.php
*
```php
namespace CPT\Reach\Application\Service\User;

use CPT\Reach\Data\Repository\User\EmailChangeRepository;

/**
 * An application service for retrieving the different emails a user has claimed.
 */
class EmailHistoryService
{
    /**
     * @var EmailChangeRepository
     */
    protected $emailChangeRepository;

    /**
     * @param EmailChangeRepository $emailChangeRepository
     */
    public function __construct(EmailChangeRepository $emailChangeRepository)
    {
        $this->emailChangeRepository = $emailChangeRepository;
    }

    /**
     * Retrieves a collection of all email addresses of a user with a given numeric id.
     *
     * @param int $id
     *
     * @return EventCollection
     */
    public function findAllByid($id)
    {
        return $this->emailChangeRepository->findAllByid($id);
    }
}
```


## Reference

* [Creating Domain Services](http://culttt.com/2014/09/29/creating-domain-services/)
