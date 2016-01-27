# Learning Log

---

## Week 1

2016-01-26
- Playing around with GitBook. Not yet settled on how I want to store/publish my notes.
    - partly inspired by John's notes: [github.com/qsymmachus/notes](https://github.com/qsymmachus/notes), I think the most valuable element of that inspiration may very well be the [learning log](learning_log.md) concept.

– Laravel/Lumen Container: manages class dependencies and aids with dependency injection, by "binding" dependency interfaces to dependency implementations. These bindings are registered in Service Providers. An instance of Container is available in all Service Providers as `app`:

```php
return new MailgunMailer($app[Credentials::class]) })
```

Any time an object has `Mailer` injected as a dependency, the Container will inject this particular instance. As illustrated above, you can resolve bindings from the Container with the following syntax:

```php
$this->app[SomeClass::class]
$this->app->make(SomeClass::class) // alternate syntax
$this->app->bind(Mailer::class, function ($app) {}
```

- playing around with using gitbooks.io to publish this repo, you can find it here: https://torsday.gitbooks.io/notebook/content/learning_log.html
