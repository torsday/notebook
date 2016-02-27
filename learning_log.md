# Learning Log

-   Run this JS at `read.amazon.com` to get copy/paste functionality *(from <https://gist.github.com/aaronshaf/1346968>)*

  ```js
  new_window=window.open();new_window.document.body.innerHTML = $('iframe').contents().find('iframe').contents().find('body').get(1).innerHTML;
  ```

2016-02-26

---

-   Set configs for an atom project across IDEs: <https://atom.io/packages/editorconfig>

-   Looking into linting my markdown

    -   [Remark Lint](https://github.com/wooorm/remark-lint), built on [Remark](https://github.com/wooorm/remark). Rules can be found [here](https://github.com/wooorm/remark-lint/blob/master/doc/rules.md)

        ```sh
        npm install --global remark remark-lint
        ```

    -   configure with `.remarkrc`

        ```json
        {
          "plugins": {
            "lint": {
              "no-multiple-toplevel-headings": true,
              "list-item-indent": true,
              "maximum-line-length": false,
              "ordered-list-marker-value": false,
              "no-duplicate-headings": false
            }
          },
          "settings": {
            "commonmark": true
          }
        }
        ```

2016-02-24

---

-   my focus has been on learning [LDAP](./internet/ldap.md) the past few days.
-   a gitbook plugin to handle checkmarks: [github.com/LingyuCoder/gitbook-plugin-todo](https://github.com/LingyuCoder/gitbook-plugin-todo)

2016-02-23

---

-   I have a love/hate relationship with Xdebug and PhpStorm. When it works, I love debugging.

2016-02-18

---

-   [vim macros](./tools/vim.md#macros)
-   Law of Demeter
-   [Exercism.IO](http://exercism.io/dashboard), a tool to learn languages.
-   symbol in ruby: an immutable value that only uses one slot of memory.
-   [Intersection / `&` in ruby](./languages/ruby.md#arrays)

2016-02-17

---

-   remove a remote repo in git

    ```sh
    git remote rm <remote_name>
    ```

-   calling a parent method in ruby:

    *From: [StackOverflow](https://stackoverflow.com/questions/18448831/calling-method-in-parent-class-from-subclass-methods-in-ruby)*

    > If the method is the same name, i.e. you're overriding a method you can simply use super. Otherwise you can use an alias_method or a binding.

    ```ruby
    class Parent
        def method
        end
    end

    class Child < Parent
        alias_method :parent_method, :method
        def method
            super
        end

        def other_method
            parent_method
            #OR
            Parent.instance_method(:method).bind(self).call
        end
    end
    ```

-   copy the contents of `id_rsa.pub` to your clipboard

    ```sh
    pbcopy < ~/.ssh/id_rsa.pub
    ```

2016-02-16

---

-   renaming a remote branch in git

    ```sh
    git remote rename origin destination
    ```

-   push to all remotes in git

    ```sh
    git remote | xargs -L1 git push --all
    ```

2016-02-15

---

-   gitbook plugin to collapse chapters: [gitbook-plugin-collapsible-menu](https://www.npmjs.com/package/gitbook-plugin-collapsible-menu). Can be found in the [GitBook Plugin Directory](https://plugins.gitbook.com/browse)

-   use [`sprintf()`](http://php.net/manual/en/function.sprintf.php) to create a template to construct a string. #PHP
    ```php
const FORMAT_MESSAGE = 'The screen name "%s" already exists.';
sprintf(static::FORMAT_MESSAGE, $screenName->getValue()));
    ```

2016-02-12

---

-   change author of last git commit

    ```sh
    git commit --amend --author="Chris Torsten <c.torsday@gmail.com>"
    ```

-   `attr_reader(*ATTR_READERS)` gets rid of never-ending arguments after `attr_reader`

-   [`{@inheritdoc}`](http://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.inlineinheritdoc.pkg.html) within a PHPDoc inherits the long description from the parent class.

2016-02-10

---

-   to get the size of a path: `$ du`

    -   `du -hs` gives just the dir it's run in
    -   [man page](http://linux.die.net/man/1/du)

-   git shallow commit

    -   [`git clone --<depth>::`](https://github.com/git/git/blob/82fba2b9d39163a0c9b7a3a2f35964cbc039e1aa/Documentation/git-clone.txt#L182-L184) creates a *shallow* clone with a truncated history to a specifed depth.
    -   Although not recommended, you can `push` and `pull` from it

2016-02-09

---

-   With an optional property (which is a class itself) within a PHP class, It's a good idea to create a Null version of the class that is returned by default if the argument is null.

    ```php
    NullMyPropClass->getValue() # returns an empty string.
    ```

    You could also return `null`, but there is value in always returning the same type.

2016-02-05

---

-   typing `f` using [vimium](https://vimium.github.io) is a great way to navigate a web page.
-   typing `f` while on a gitbook page brings up search.

2016-02-04

---

-   [Kitematic](https://kitematic.com), a nice tool to interact with your docker images.
-   Playing around with [Huginn](https://github.com/cantino/huginn), an interesting agent tool, like IFTTT ([here's a nice video](https://vimeo.com/61976251)). ...pretty sure it's logo and name alude to one of my favorite authors, [Daniel Suarez](http://www.goodreads.com/author/show/1956402.Daniel_Suarez).

2016-02-03

---

-   [http://readable.tastefulwords.com/](http://readable.tastefulwords.com) Great tool to make a site readable.

-   Phing *(PHing Is Not GNU make)*

    > it's a PHP project build system or build tool based on ​Apache Ant. You can do anything with it that you could do with a traditional build system like GNU make, and its use of simple XML build files and extensible PHP "task" classes make it an easy-to-use and highly flexible build framework.

-   To zero out a css transform, which you may want to do if it leaves junk pixels...

    ```css
    .modal-shadow .modal {
        -webkit-transform: none;
        transform: none;
    }
    ```

2016-02-02

---

-   Interetesting article (<https://speakerdeck.com/vjeux/react-css-in-js>) about inlining styles in React.
-   TODO process notes from <https://stash.corp.creditkarma.com/projects/MAX/repos/admax-js/pull-requests/141/overview>

2016-02-01

---

## Week of 2016-02-01

---

Switching to a Twitter-esque sorting

---

Learning Log

---

## Week of 2016-01-25

---

2016-01-26

-   Playing around with GitBook. Not yet settled on how I want to store/publish my notes.

  partly inspired by John's notes: [github.com/qsymmachus/notes](https://github.com/qsymmachus/notes), I think the most valuable element of that inspiration may very well be the [learning log](learning_log.md) concept.

-   Laravel/Lumen Container: manages class dependencies and aids with dependency injection, by "binding" dependency interfaces to dependency implementations. These bindings are registered in Service Providers. An instance of Container is available in all Service Providers as `app`:

  ```php
  return new MailgunMailer($app[Credentials::class]) })
  ```

  Any time an object has `Mailer` injected as a dependency, the Container will inject this particular instance. As illustrated above, you can resolve bindings from the Container with the following syntax:

  ```php
  $this->app[SomeClass::class]
  $this->app->make(SomeClass::class) // alternate syntax
  $this->app->bind(Mailer::class, function ($app) {}
  ```

-   playing around with using gitbooks.io to publish this repo, you can find it here: <https://torsday.gitbooks.io/notebook/content/learning_log.html>

---

2016-01-27

-   To commit case-sensitive only filename changes in Git:

  ```bash
  git config core.ignorecase false
  ```

  see [StackOverflow: 17683458](http://stackoverflow.com/questions/17683458/how-do-i-commit-case-sensitive-only-filename-changes-in-git)

---

2016-01-28

-   When you use ```EventCollection``` with an iteration operator such as ```foreach```, it pops each element off, destroying the data structure. You may need to use ```clone```:

    ```php
    foreach (clone $this->accountStatusEvents as $e) {
        $serializedEvents[] = EventJsonSerializerFactory::create($e);
    }
    ```

-   ```$this->assertCount($expectedInt, $countableObj);```

  ```php
  $eventCollection = new EventCollection();
  $count           = count($eventCollection); // 0
  ```

  How it works: ```EventCollection``` extends ```Collection``` which extends ```SplMaxHeap``` (<http://php.net/manual/en/class.splmaxheap.php>) which implements ```Countable``` (<http://php.net/manual/en/class.countable.php>).

-   Private functions should be positioned below public ones in PHP.

-   upgrade npm packages

    > Identify out of date packages (```npm outdated```). Update the versions in your ```package.json```. Run ```npm update``` to install the latest versions of each package.

-   font awesome has a nice [history icon](http://fortawesome.github.io/Font-Awesome/icon/history)

-   to make an image appear in markdown, make a link with an exclamation point prepended to it.

    ```markdown
    ![Local Image](./images/<image_file_name>)
    ```

-   CSS to use system fonts on mobile devices:

  ```css
  font-family: system, -apple-system, ".SFNSText-Regular", "San Francisco", "Roboto", "Segoe UI", "Helvetica Neue", "Lucida Grande", sans-serif;
  ```

-   Sleep display

  ```bash
  pmset displaysleepnow
  ```

-   empty directories

  ```bash
  # list
  find . -type d -empty -print

  # delete
  find . -type d -empty -delete
  ```

-   git branch authors

  ```bash
  git for-each-ref --format='%(committerdate)%09%(authorname)%09%(refname)' | sort -k5n -k2M -k3n -k4n | grep remotes | awk -F "\t" '{ printf "%-32s %-27s %s\n", $1, $2, $3 }'
  ```

-   git merged remote branches

  ```bash
  for branch in `git branch -r --merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
  ```

-   git un-merged remote branches

  ```bash
  for branch in `git branch -r --no-merged | grep -v HEAD`; do echo -e `git show --format="%ci %cr %an" $branch | head -n 1` \\t$branch; done | sort -r
  ```

-   rename extensions of files in a dir

  ```bash
  find . -name "*.rb" -exec bash -c 'mv "$1" "$(sed "s/\.rb$/.md/" <<< "$1")"' - '{}' \;
  ```

2016-01-29

-   `Shift+Esc` to clear all slack channel notifications

TODO: outline likely CK files to create

-   kamino/modal

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

-   git stage part of file

    ```bash
    git add -p
    ```

-   TODO bind in Javascript

-   Reminded about how useful inserting `debugger` into my JS code can be when combined with Chrome.

---
