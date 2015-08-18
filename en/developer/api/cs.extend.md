# API cs.extend

### cs.extend.addAutocompletion(configuration)

* **Description**: Extend Ctrl-Space autocompletions. 

* **Parameter**:
    * *Object* configuration - configuration params:
        * configuration.name: the code completion name (e.g. margin-top)
        * configuration.scope: the file scope (e.g. text/css)
        * configuration.onSelect: callback executed when code completion is selected
        * configuration.onBlur: callback executed when leaving code completion item
        * configuration.onSubmit: callback executed code completion item is triggered

* **Return**: null

### cs.extend.addSimplifier(configuration)

* **Description**: Create new Clickable Simplifiers.

* **Parameter**:
    * *Object* configuration - configuration params:
        * configuration.name: the simplifier name (e.g. create-image)
        * configuration.onRun: method called on simplifier execution

* **Return**: null