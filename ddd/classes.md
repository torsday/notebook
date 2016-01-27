# Classes


## Domain

* [Model](model.md)
    * Collection
* [Repository](repository.md)
* [Service](service.md)


## Platform

* RAML
* Serializer
* collectionSerializer
* route
* controller
* Service Provider (that uses mocks)


## CPT

* Repository
    ```bash
EmailChangeTbl #(CPT original, taps DB)
CptTblEmailHistoryRepository
CptTblEmailHistoryRepositoryTest
    ```
* Adapter
* [Service Provider](service-providers.md) (that plugs into CPT)
    ```bash
CptAppServiceProvider
# or
CptEmailHistoryServiceProvider
    register()
    ```


## URL to Path Tree mapping

```
CPT.com                    /admin/            users/          view/id/1234
docroot/application/modules/admin/controllers/UsersController#ViewAction
```
