# jade-to-jsx

A very hacky converter for jade files to react components.

Handles very basic variables in jade, e.g. `p= foo` by converting to props as appropriate, but currently trips over a lot of cases.

## Install
```shell
npm install -g jade-to-jsx
jade-to-jsx test.jade > Test.js
```

## Example

```shell
jade-to-jsx test.jade > Test.js
```

Will convert:

```jade
h1 Hello
p= foo
p= foo*2
p= bar.baz

include ./bar.jade
```

```javascript
import React from 'React';

export default React.createClass({
  propTypes: {
    bar: React.PropTypes.any,
    foo: React.PropTypes.any
  },
  render() {
    let { bar, foo } = this.props;

    return (
      <div>
        <h1>Hello</h1>
        <p>{foo}</p>
        <p>{foo*2}</p>
        <p>{bar.baz}</p>
        <h2>Bar</h2>
      </div>
    );
  }
});
```

### Contributing

Umm, sorry about the code? Very messy hack rn.

### License

MIT
