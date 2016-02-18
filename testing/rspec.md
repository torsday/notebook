# Rspec



*From: [Wikipedia](https://en.wikipedia.org/wiki/RSpec)*
> A behavior-driven development (BDD) framework for the Ruby programming language, inspired by JBehave. It contains its own mocking framework that is fully integrated into the framework based upon JMock. The framework can be considered a domain-specific language (DSL) and resembles a natural language specification.

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


## References

* [Better Specs { rspec guidelines with ruby }](http://betterspecs.org/)


## See Also

* [Factory Girl](https://github.com/thoughtbot/factory_girl)
