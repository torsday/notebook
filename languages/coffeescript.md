# CoffeeScript

## Examples

```coffeescript
MyPackageView = require './my-package-view'

module.exports =
  myPackageView: null

  activate: (state) ->
    @myPackageView = new MyPackageView(state.myPackageViewState)

  deactivate: ->
    @myPackageView.destroy()

  serialize: ->
    myPackageViewState: @myPackageView.serialize()
```

## References

-   [CoffeeScript.org](http://coffeescript.org/)
