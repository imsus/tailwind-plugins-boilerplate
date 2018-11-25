# Sample Plugin Without Params

This module demonstrate on how to create a plugin that doesn't accept any params. Also, this plugin utilize the `addComponents()` feature which generate `.btn`, `.btn-blue`, and `.btn-red` classes.

## Usage

### Input

Your sample plugin file the content is precisely same with `index.js` in this folder.

`index.js`

```javascript
module.exports = function ({ addComponents }) {
  const buttons = {
    '.btn': {
      padding: '.5rem 1rem',
      borderRadius: '.25rem',
      fontWeight: '600',
    },
    '.btn-blue': {
      backgroundColor: '#3490dc',
      color: '#fff',
      '&:hover': {
        backgroundColor: '#2779bd'
      },
    },
    '.btn-red': {
      backgroundColor: '#e3342f',
      color: '#fff',
      '&:hover': {
        backgroundColor: '#cc1f1a'
      },
    },
  }

  addComponents(buttons)
}
```

### Registering Plugin

On your `tailwind.js` configuration file:

```javascript
module.exports = {
    // ..Previous Code

    plugins: [
        // Your path to plugin file
        require('./src/sample-plugin-without-params/index.js'),
    ],

    // ..Next Code
}
```

### Output

Since it only uses `addComponents()` function, the generated output will be placed on `@tailwind components;` section.

```css
/* Generated `@tailwind preflight;` CSS */

/* -----------------------------------------------------------
Generated `@tailwind components;` CSS including your plugins.
----------------------------------------------------------- */

.btn {
    padding: .5rem 1rem;
    border-radius: .25rem;
    font-weight: 600;
}

.btn-blue {
    background-color: #3490dc;
    color: #fff;
}

.btn-blue:hover {
    background-color: #2779bd;
}

.btn-red {
    background-color: #e3342f;
    color: #fff;
}

.btn-red:hover {
    background-color: #cc1f1a;
}

/* -----------------------------------------------------------
End of `@tailwind components;` generated CSS
----------------------------------------------------------- */

/* Generated @tailwind utilities; CSS */
```
