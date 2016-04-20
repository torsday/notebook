# Learning Log

---

setting a specific port with `gitbook serve`:

```sh
gitbook --port 3000 serve
```

---

Created a HSTS entry. [Wikipedia article](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security)

---

2016-04-18

---

Create symlinks for appropriate brew apps

```sh
brew linkapps <app_name_or_blank>
```

---

Experimenting with Emacs because I'm interested in org-mode.

[StackOverflow: What is the difference between Aquamacs and other Mac versions of Emacs?](http://emacs.stackexchange.com/questions/271/what-is-the-difference-between-aquamacs-and-other-mac-versions-of-emacs)

```sh
brew install emacs --HEAD --use-git-head --with-cocoa --with-gnutls --with-rsvg --with-imagemagick
```

---

-   [Akka](http://akka.io)

-   spray routes: <http://spray.io/documentation/1.1.2/spray-routing/>

-   [ScalaTest](http://www.scalatest.org)

-   *From: [Akka: actor system](http://doc.akka.io/api/akka/2.0/akka/actor/ActorSystem.html)*

    > An actor system is a hierarchical group of actors which share common configuration, e.g. dispatchers, deployments, remote capabilities and addresses. It is also the entry point for creating or looking up actors.

2016-04-13

---

-   Gitbook, within `SUMMARY`

-   CAN-SPAM Act of 2003

    -   > The CAN-SPAM Act of 2003, signed into law by President George W. Bush on December 16, 2003, establishes the United States' first national standards for the sending of commercial e-mail and requires the Federal Trade Commission (FTC) to enforce its provisions.
    -   Why emails need an unsubscribe link in emails.
    -   [Wikipedia Link](https://en.wikipedia.org/wiki/CAN-SPAM_Act_of_2003)

2016-04-11

---

-   `chmod 755 <script_name>` making a ruby script executable

2016-03-29

---

-   `array_filter()`

2016-03-25

---

-   `foreach()` in PHP is destructive; clone the enumerable prior to use:

    ```php
    foreach(clone $myStuff as $thing) {...};
    ```

2016-03-22

---

-   Namespace leaks with a `foreach()` loop in PHP

    ```php
    $testVar = ['yo', 'mario'];

    foreach($testVar as $t) {}

    echo $t;
    ```

    ```php
    mario
    ```

-   > **Kintsugi** (金継ぎ?) (Japanese: golden joinery) or Kintsukuroi (金繕い?) (Japanese: golden repair) is the Japanese art of repairing broken pottery with lacquer dusted or mixed with powdered gold, silver, or platinum, a method similar to the maki-e technique. As a philosophy it **treats breakage and repair as part of the history of an object, rather than something to disguise**.
    > <https://en.wikipedia.org/wiki/Kintsugi>

    ![Kintsugi Bowl](https://diotesterie.files.wordpress.com/2016/02/kintsugi.jpg)

-   > **Kaizen** (Continuous Improvement) is a strategy where employees at all levels of a company work together proactively to achieve regular, incremental improvements to the manufacturing process. In a sense, it combines the collective talents within a company to create a powerful engine for improvement.
    > <http://www.leanproduction.com/kaizen.html>

2016-03-21

---

-   In PHP, using the `final` keyword with a class or method prevents child classes from overriding it, whether with a new method declaration or a class extesion. *([PHP.net](http://php.net/manual/en/language.oop5.final.php))*

    ```php
    <?php
    final class BaseClass {
       public function test() {
           echo "BaseClass::test() called\n";
       }

       // Here it doesn't matter if you specify the function as final or not
       final public function moreTesting() {
           echo "BaseClass::moreTesting() called\n";
       }
    }

    class ChildClass extends BaseClass {
    }
    // Results in Fatal error: Class ChildClass may not inherit from final class (BaseClass)
    ?>
    ```

-   In PHP, [`array_key_exists()`](http://php.net/manual/en/function.array-key-exists.php) will tell you if a key exists in an array, [`isset()`](http://php.net/manual/en/function.isset.php) will only return `true` if the key/variable exists and is not `null`.

2016-03-17

---

-   Grabbing command line arguments from a PHP script

    -   `getopt` *([php.net](http://php.net/manual/en/function.getopt.php))*

    ```php
    $shortopts  = "";
    $shortopts .= "f:";  // Required value
    $shortopts .= "v::"; // Optional value
    $shortopts .= "abc"; // These options do not accept values

    $longopts  = array(
        "required:",     // Required value
        "optional::",    // Optional value
        "option",        // No value
        "opt",           // No value
    );
    $options = getopt($shortopts, $longopts);
    ```

    ```sh
    php example.php -f "value for f" -v -a --required value --optional="optional value" --option
    ```

    ```php
    array(6) {
      ["f"]=>
      string(11) "value for f"
      ["v"]=>
      bool(false)
      ["a"]=>
      bool(false)
      ["required"]=>
      string(5) "value"
      ["optional"]=>
      string(14) "optional value"
      ["option"]=>
      bool(false)
    }
    ```

2016-03-16

---

-   Parse a csv file in PHP (from [php.net](http://php.net/manual/en/function.str-getcsv.php))

    ```php
    $csv = array_map('str_getcsv', file('data.csv'));
    ```

-   What I've worked on recently:

    -   [Curl](./linux/curl.md)
    -   [Docker](./dev_ops/docker.md)
    -   [Domain Driven Development](./design/ddd.md)
    -   [Foreman](./dev_ops/foreman.md)
    -   [Functional Programming](./design/functional.md)
    -   [Jenkins](./dev_ops/jenkins.md)
    -   [Onion Architecture](./design/onion.md)
    -   [Sumatriptan](./medicine/pharmacology/drugs/sumatriptan.md)
    -   [Symbicort](./medicine/pharmacology/drugs/symbicort.md)
    -   [Terraform](./dev_ops/terraform.md)
    -   [UML](./tools/uml.md)
    -   [Vagrant](./dev_ops/vagrant.md)
    -   [XHProf](./languages/php/xhprof.md)

2016-03-15

---

-   Change mode to be executable: `chmod +x <file>`; nothing new here, but I thinking of it as chmod, not change mode. I think the latter will be easier to remember.

-   paste this into your browser console to beautify formatting

    ```js
    var sheet = document.createElement('style');
    sheet.innerHTML = "body{margin: 40px auto;max-width: 650px;line-height: 1.5;font-size: 18px;color: #3a3a3a;padding: 0 10px;}";
    document.body.appendChild(sheet);
    ```

2016-03-14

---

-   UML diagram w/i PhpStorm:

    1.  install plugin (it's the only UML one)
    2.  select dir
    3.  `⇧` + `⌥` + `⌘` + `u`

-   git: show files updated/created in the past x days

    ```sh
    git log --pretty=format: --name-only --since="3 days ago" | sort | uniq
    ```

-   What I've worked on recently:

    -   [Buddhism](./lifestyle/buddhism.md)
    -   [Git](./tools/git/README.md)
    -   [PHP Autoloader](./php/autoloader.md)
    -   [RAML](./languages/raml.md)
    -   [Ruby `throw` vs `raise`](./languages/ruby/throw_vs_raise.md)
    -   [Swift](./languages/swift.md)
    -   [UML](./tools/uml.md)

2016-03-07

---

-   Run this JS at [read.amazon.com](https://read.amazon.com) to get copy/paste functionality *(from <https://gist.github.com/aaronshaf/1346968>)*

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
-   [Intersection / `&` in ruby](./languages/ruby/README.md#arrays)

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
