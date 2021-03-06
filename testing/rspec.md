# Rspec

---

A behavior-driven development (BDD) framework for Ruby.

-   Domain-specific language (DSL)
-   Resembles a natural language specification

```ruby
#Testing for our User class
describe User do
  context 'with admin privileges' do
    before :each do
      @admin = Admin.get(1)
    end

    it 'should exist' do
      expect(@admin).not_to be_nil
    end

    it 'should have a name' do
      expect(@admin.name).not_to be_false
    end
  end

  #...
end
```

---

## Bits of Knowledge

### Disable a tree of specs

#### Rspec 3

```ruby
before { skip }
```

or

```ruby
xdescribe
```

#### Rspec 2

```ruby
before { pending }
```

or

```ruby
context 'login as user' do
  before do
    pending "Skipped until CKVM is updated with necessary Vault data for this functionality to work."
  end

  # ...

end
```

---

## Relevant Gems

-   [Better Errors](https://github.com/charliesome/better_errors)
-   [Factory Girl](https://github.com/thoughtbot/factory_girl)

---

## References

-   [Better Specs](http://betterspecs.org)
-   [Wikipedia: Rspec](https://en.wikipedia.org/wiki/RSpec)
