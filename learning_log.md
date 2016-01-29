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

- font awesome has a nice [history icon](http://fortawesome.github.io/Font-Awesome/icon/history/)

- to make an image appear in markdown, make a link with an exclamation point prepended to it.

  ```markdown
  ![Local Image](./images/<image_file_name>)
  ```

- CSS to use system fonts on mobile devices:

  ```css
  font-family: system, -apple-system, ".SFNSText-Regular", "San Francisco", "Roboto", "Segoe UI", "Helvetica Neue", "Lucida Grande", sans-serif;
  ```

- Sleep display

  ```bash
  pmset displaysleepnow
  ```

- empty directories

  ```bash
  # list
  find . -type d -empty -print

  # delete
  find . -type d -empty -delete
  ```

- git branch authors

  ```bash
  git for-each-ref --format='%(committerdate)%09%(authorname)%09%(refname)' | sort -k5n -k2M -k3n -k4n | grep remotes | awk -F "\t" '{ printf "%-32s %-27s %s\n", $1, $2, $3 }'
  ```

- git merged remote branches

  ```bash
  for branch in `git branch -r --merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
  ```

- git un-merged remote branches

  ```bash
  for branch in `git branch -r --no-merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
  ```

- rename extensions of files in a dir

  ```bash
  find . -name "*.rb" -exec bash -c 'mv "$1" "$(sed "s/\.rb$/.md/" <<< "$1")"' - '{}' \;
  ```

2016-01-29

- `Shift+Esc` to clear all slack channel notifications

TODO: outline likely CK files to create

- kamino/modal

    ```js
    // JSX
    return (
        <Modal
            nox
            ref="something"
        >
            content
        </Modal>
    );

    // Javascript ES6
    this.refs.something.show(); -> show modal
    this.refs.something.hide(); -> hide modal
    ```

- git stage part of file

    ```bash
    git add -p
    ```

- TODO bind in Javascript
