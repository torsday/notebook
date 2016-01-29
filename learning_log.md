# Learning Log

---

## Week of 2016-01-25

---

2016-01-26

- Playing around with GitBook. Not yet settled on how I want to store/publish my notes.

  partly inspired by John's notes: [github.com/qsymmachus/notes](https://github.com/qsymmachus/notes), I think the most valuable element of that inspiration may very well be the [learning log](learning_log.md) concept.

- Laravel/Lumen Container: manages class dependencies and aids with dependency injection, by "binding" dependency interfaces to dependency implementations. These bindings are registered in Service Providers. An instance of Container is available in all Service Providers as `app`:

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


---

2016-01-27

TODO: factory

TODO: phing

- To commit case-sensitive only filename changes in Git:

  ```bash
  git config core.ignorecase false
  ```

  see [StackOverflow: 17683458](http://stackoverflow.com/questions/17683458/how-do-i-commit-case-sensitive-only-filename-changes-in-git)

---

2016-01-28

- When you use ```EventCollection``` with an iteration operator such as ```foreach```, it pops each element off, destroying the data structure. You may need to use ```clone```:

```php
foreach (clone $this->accountStatusEvents as $e) {
    $serializedEvents[] = EventJsonSerializerFactory::create($e);
}
```

- ```$this->assertCount($expectedInt, $countableObj);```

  ```php
  $eventCollection = new EventCollection();
  $count           = count($eventCollection); // 0
  ```

  How it works: ```EventCollection``` extends ```Collection``` which extends ```SplMaxHeap``` (http://php.net/manual/en/class.splmaxheap.php) which implements ```Countable``` (http://php.net/manual/en/class.countable.php).

- Private functions should be positioned below public ones in PHP.

- upgrade npm packages

  > Identify out of date packages (```npm outdated```). Update the versions in your ```package.json```. Run ```npm update``` to install the latest versions of each package.
