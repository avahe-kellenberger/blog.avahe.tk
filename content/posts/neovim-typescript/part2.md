---
title: "Setting up Neovim for Typescript - Part 2"
date: 2020-04-07T19:04:27-04:00
draft: false
---

# Topic: Setting up eslint and prettier

Part 2 will focus on [eslint](https://eslint.org/) and [prettierjs](https://prettier.io/) configuration.

`eslint` enforces syntax rules, while `prettier` is more focused on code formatting.

### tl;dr / I am an experienced (neo)vim user

Install [coc-eslint](https://github.com/neoclide/coc-eslint#coc-eslint) using `g:coc_global_extensions`

# Getting Started

## coc-eslint

In part one we declared a variable named `g:coc_global_extensions` in our `~/.config/nvim/init.vim` file. In order to install this new CoC extension, add `'coc-eslint'` to the array as shown below.

Be sure to include the comma after `'coc-tsserver'`

```VimL

" Declare CoC extensions
let g:coc_global_extensions = [
  \ 'coc-tsserver',
  \ 'coc-eslint'
  \ ]

```

That's it! Next time you start up neovim, CoC will automatically install `coc-eslint`

## Configuring our example project

Check out ["Getting Start - Linting your TypeScript Codebase"](https://github.com/typescript-eslint/typescript-eslint/blob/master/docs/getting-started/linting/README.md#getting-started---linting-your-typescript-codebase) for more details and configuration options.

You may follow along for an example setup, or skip the next section.

### Example eslint configuration

Let's move into our project and start installing our eslint dependencies:

```Bash

$ yarn add -D eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser

```

These Typescript eslint plugins are used to parse Typescript's syntax, and allow for us to set up linting rules which only apply to Typescript (and not vanilla Javascript).


Let's create a basic eslint configuration file, `.eslintrc.json`:

```JSON

{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended"
  ]
}

```

## **The list of typescript specific rules can be found [here](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin#supported-rules).**

Now we should have proper eslint warnings and errors for our project. Play with the existing code and give it a try!

### Example prettierjs configuration

Next, if you would like to add prettier into the mix, install the following:

```Bash

$ yarn add -D prettier eslint-config-prettier eslint-plugin-prettier

```

We will now add a basic prettier config file, `.prettierrc.json`:

```JSON

{
  "semi": true,
  "trailingComma": "none",
  "singleQuote": true,
  "printWidth": 120,
  "tabWidth": 2
}

```

One last thing to change, is to add the prettier plugin to our `.eslintrc.json` (bottom):

```JSON

{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:prettier/recommended"
  ]
}

```

Now, Neovim is set up to apply eslint and prettierjs linting and formatting rules!

**One thing to note about this particular setup**: The rules defined in your prettierjs configuration will override any similar formatting rules defined in your eslint configuration.

