# Domain Driven Design

Handles complexity by connecting the implementation to an evolving model.

Premise:

-   Placing the project's primary focus on the core domain and domain logic.
-   Basing complex designs on a model of the domain.
-   Initiating a creative collaboration between technical and domain experts to iteratively refine a conceptual model that addresses particular domain problems.

> Domain Driven Design places development focus primarily on the unique *business rules* which an application unique. This means codifying business rules in Domain Entities, Value Objects and Services, in a layer that is separate from other focuses such as infrastructure and persistence requirements. The structure of the Reach PHP package can serve as a good example of how to organize your code.

> ~ Robert Van Dell

---

**Table of Contents**

<!--lint disable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

<!-- TOC depthFrom:2 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Architecture](#architecture)
	- [**Domain** layer](#domain-layer)
	- [**Application** layer](#application-layer)
	- [**Infrastructure** layer](#infrastructure-layer)
- [Classes](#classes)
	- [Domain](#domain)
	- [Platform](#platform)
	- [Application](#application)
- [or](#or)
	- [URL to Path Tree mapping](#url-to-path-tree-mapping)
- [Model](#model)
	- [e.g. ```EmailChange.php```](#eg-emailchangephp)
- [Repository](#repository)
	- [e.g. ```EmailChangeRepository.php```](#eg-emailchangerepositoryphp)
	- [Reference](#reference)
- [Service](#service)
	- [Types of Service](#types-of-service)
	- [e.g. ```EmailHistoryService.php```](#eg-emailhistoryservicephp)
	- [Reference](#reference)
- [Service Providers](#service-providers)

<!-- /TOC -->

<!--lint enable list-item-indent list-item-spacing no-missing-blank-lines no-tabs-->

---

## Concepts

|                     |                                                                                                                                               |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Context             | The setting in which a word or statement appears that determines its meaning.                                                                 |
| Domain              | A sphere of knowledge (ontology), influence, or activity. The subject area to which the user applies a program is the domain of the software. |
| Model               | A system of abstractions that describes selected aspects of a domain and can be used to solve problems related to that domain.                |
| Ubiquitous Language | A language structured around the domain model and used by all team members to connect all the activities of the team with the software.       |

## Building Blocks

| x            | y                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------:|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Entity       | An object that is not defined by its attributes, but rather by a thread of continuity and its identity. Example: Most airlines distinguish each seat uniquely on every flight. Each seat is an entity in this context. However, Southwest Airlines, EasyJet and Ryanair do not distinguish between every seat; all seats are the same. In this context, a seat is actually a value object.                                                                                                                                                                                            |
| Value Object | An object that contains attributes but has no conceptual identity. They should be treated as immutable. Example: When people exchange dollar bills, they generally do not distinguish between each unique bill; they only are concerned about the face value of the dollar bill. In this context, dollar bills are value objects. However, the Federal Reserve may be concerned about each unique bill; in this context each bill would be an entity.                                                                                                                                 |
| Aggregate    | A collection of objects that are bound together by a root entity, otherwise known as an aggregate root. The aggregate root guarantees the consistency of changes being made within the aggregate by forbidding external objects from holding references to its members. Example: When you drive a car, you do not have to worry about moving the wheels forward, making the engine combust with spark and fuel, etc.; you are simply driving the car. In this context, the car is an aggregate of several other objects and serves as the aggregate root to all of the other systems. |
| Domain Event | A domain object that defines an event (something that happens). A domain event is an event that domain experts care about.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Service      | When an operation does not conceptually belong to any object. Following the natural contours of the problem, you can implement these operations in services. See also Service (systems architecture).                                                                                                                                                                                                                                                                                                                                                                                 |
| Repository   | Methods for retrieving domain objects should delegate to a specialized Repository object such that alternative storage implementations may be easily interchanged.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Factory      | Methods for creating domain objects should delegate to a specialized Factory object such that alternative implementations may be easily interchanged.                                                                                                                                                                                                                                                                                                                                                                                                                                 |

## Architecture

### **Domain** layer

Where the business logic of the application resides. As we’ve seen over the last couple of weeks, this is where you have Domain Objects (i.e. models) such as your ```User``` Entity or ```Email``` and ```Username``` Value Objects.

### **Application** layer

How the outside world communicates with the model.

e.g. HTTP requests, an API or through an automated messaging service.

### **Infrastructure** layer

How the actions of the model are executed.

e.g. persisting data to a database, queuing jobs, or sending email notifications.

---

## Classes

### Domain

-   [Model](model.md)


    -   Collection

-   [Repository](repository.md)


-   [Service](service.md)

### Platform

-   RAML
-   Serializer
-   collectionSerializer
-   route
-   controller
-   Service Provider (that uses mocks)

### Application

-   Repository

      ```bash
      EmailChangeTbl #(CPT original, taps DB)
      CptTblEmailHistoryRepository
      CptTblEmailHistoryRepositoryTest
      ```

-   Adapter

-   [Service Provider](service-providers.md) (that plugs into CPT)

    ```bash
    CptAppServiceProvider
    ```

    or

    ```sh
    CptEmailHistoryServiceProvider
    register()
    ```

### URL to Path Tree mapping

```sh
CPT.com                    /admin/            users/          view/id/1234
docroot/application/modules/admin/controllers/UsersController#ViewAction
```

---

## Model

### e.g. ```EmailChange.php```

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

---

## Repository

> A system with a complex domain model often benefits from a layer, such as the one provided by Data Mapper, that isolates domain objects from details of the database access code. In such systems it can be worthwhile to build another layer of abstraction over the mapping layer where query construction code is concentrated. This becomes more important when there are a large number of domain classes or heavy querying. In these cases particularly, adding this layer helps minimize duplicate query logic.

> **A Repository mediates between the domain and data mapping layers, acting like an in-memory domain object collection.** Client objects construct query specifications declaratively and submit them to Repository for satisfaction. Objects can be added to and removed from the Repository, as they can from a simple collection of objects, and the mapping code encapsulated by the Repository will carry out the appropriate operations behind the scenes. Conceptually, a Repository encapsulates the set of objects persisted in a data store and the operations performed over them, providing a more object-oriented view of the persistence layer. Repository also supports the objective of achieving a clean separation and one-way dependency between the domain and data mapping layers.

### e.g. ```EmailChangeRepository.php```

*reach-php/src/CPT/Reach/Data/Repository/User/EmailChangeRepository.php*

```php
namespace CPT\Reach\Data\Repository\User;

/**
 * A consistent interface for encapsulating the persistence responsibilities of a user's email history.
 */
interface EmailChangeRepository
{
    /**
     * Retrieves all of a user's past emails by numeric id.
     *
     * @param int $id
     *
     * @return \CPT\Common\Domain\Model\EventCollection
     */
    public function findAllByid($id);
}
```

### Reference

-   <http://martinfowler.com/eaaCatalog/repository.html>

---

## Service

A Service in Domain Driven Design is simply a stateless object that performs an action.

### Types of Service

1.  **Application Service** is typically used to orchestrate how the outside world interacts with your application. For example ```AuthenticationService``` would be an Application Service that co-ordinates how a user should be authenticated.
1.  **Infrastructure Service** is used for dealing with the technical details of the infrastructure. For example you might have a ```MailGunMessenger``` service that enables you to send email notifications using the MailGun API.
1.  **Domain Service** is used for encapsulating domain logic that does not naturally fit on any existing Domain Object. For example you might have a ```RegisterUserService``` that co-ordinates how a user is registered within your application.

### e.g. ```EmailHistoryService.php```

*reach-php/src/CPT/Reach/Application/Service/User/EmailHistoryService.php*

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

### Reference

-   [Creating Domain Services](http://culttt.com/2014/09/29/creating-domain-services/)

---

## Service Providers
