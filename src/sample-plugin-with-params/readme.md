# Sample Plugin With Params

This module demonstrate on how to create a plugin that accept some params. Also, this plugin utilize the `addUtilities()` feature which will generate `.bg-gradient-${name}` classes (where `${name}` is generated from parameter).

## Usage

### Input

Your sample plugin file the content is precisely same with `index.js` in this folder.

`index.js`

```javascript
const map = require('lodash.map');

module.exports = function ({ gradients, variants }) {
  return function ({ addUtilities, e }) {
    const utilities = map(gradients, ([start, end], name) => ({
      [`.bg-gradient-${e(name)}`]: {
        backgroundImage: `linear-gradient(to right, ${start}, ${end})`
      }
    }));

    addUtilities(utilities, variants);
  };
};

```

### Registering Plugin

On your `tailwind.js` configuration file:

```javascript
module.exports = {
    // ..Previous Code

    plugins: [
        // Your path to plugin file with parameter
        require('./src/sample-plugin-with-params/index.js')({
            // Don't forget the parameter
            gradients: {
                'blue-green': ['blue', 'rgb(0, 255, 0)'],
                'purple-blue': ['purple', '#00f'],
                // ...
            },
            variants: ['hover'],
        }),
    ],

    // ..Next Code
}
```

### Output

Since the module needs parameter, the generated CSS will be based on the parameter itself. Also since it use `addUtilities()` method, the generated CSS will be placed on the `@tailwind utilities;` section

```css
/* Generated `@tailwind preflight;` CSS */

/* Generated `@tailwind components;` CSS */

/* -----------------------------------------------------------
Generated `@tailwind utilities;` CSS including your plugins.
----------------------------------------------------------- */

.bg-gradient-blue-green {
    background-image: linear-gradient(to right, blue, rgb(0, 255, 0));
}

.hover\:bg-gradient-blue-green:hover {
    background-image: linear-gradient(to right, blue, rgb(0, 255, 0));
}

.bg-gradient-purple-blue {
    background-image: linear-gradient(to right, purple, #00f);
}

.hover\:bg-gradient-purple-blue:hover {
    background-image: linear-gradient(to right, purple, #00f);
}

/* -----------------------------------------------------------
End of `@tailwind utilities;` generated CSS
----------------------------------------------------------- */
```
