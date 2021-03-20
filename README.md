![nuxt-windicss](https://repository-images.githubusercontent.com/343991410/68f83b80-811f-11eb-9638-51aed75785c4)

<h1 align='center'>nuxt-windicss</h1>

<p align='center'><a href="https://github.com/windicss/windicss">Windi CSS</a> for Nuxt.js, it's fast! ⚡️<br>
<sup><em>a.k.a On-demand Tailwind CSS</em></sup>
</p>

<p align='center'>
<a href='https://www.npmjs.com/package/nuxt-windicss'>
<img src='https://img.shields.io/npm/v/nuxt-windicss?color=0EA5E9&label='>
</a>
</p>

<p align='center'>
<a href='https://twitter.com/antfu7/status/1361398324587163648'>⚡️ See speed comparison with Tailwind</a>
</p>

## Features

- ⚡️ **It's FAST** - 20~100x times faster than [@nuxtjs/tailwindcss](https://github.com/nuxt-community/tailwindcss-module)
- 🧩 On-demand CSS utilities (Compatible with Tailwind CSS v2) and native elements style resetting
- 🍃 Load configurations from `tailwind.config.js`
- 📄 CSS `@apply` / `@screen` directives transforms
- 🎳 Support Utility Groups - e.g. `bg-gray-200 hover:(bg-gray-100 text-red-300)`
- 🧑‍🤝‍🧑 Compatible with [nuxt-vite](https://github.com/nuxt/vite)

## Install

```bash
yarn add nuxt-windicss -D
# npm i nuxt-windicss -D
```

:warning: This module is a pre-release, please report any [issues](https://github.com/windicss/nuxt-windicss-module/issues) you find.

## Usage

Within your `nuxt.config.js` add the following.

```js
// nuxt.config.js
buildModules: [
  'nuxt-windicss',
],
```

This module won't work with `@nuxtjs/tailwindcss`, you will need to remove it.

```diff
buildModules: [
-  '@nuxtjs/tailwindcss',
],
```

If you have a `tailwind.config.js`, please rename it to `windi.config.js`.

This module will read from `windi.config.js` config if present. See [here](https://windicss.netlify.app/guide/configuration.html) for details.


## Migrating

If you were previously using `@nuxtjs/tailwindcss`, please consult the [documentation](https://windicss.netlify.app/guide/migration.html) on migrating.

## Configuration

- Default:
```js
windicss: {
  scan: {
    dirs: ['./'],
      exclude: [
        '.nuxt/**/*',
        '*.template.html',
        // Any classes added in app.html (that have not previously been referenced) will need to be added to the safelist
        'app.html'
      ]
  },
  transformCSS: 'pre',
  preflight: {
    alias: {
      // add nuxt aliases
      'nuxt-link': 'a',
    }
  }
}
```  

- See [options.ts](https://github.com/windicss/vite-plugin-windicss/blob/main/packages/plugin-utils/src/options.ts) for configuration reference.

### Examples

#### Disable Preflight

_nuxt.config.js_
```js
export default {
  // ...
  windicss: {
    preflight: false
  },
}  
```

## Hooks

You can use the following nuxt hooks to modify the behaviour of the code.

`windicss:config`
- Arguments: options

Modify the windicss configuration before it is passed to the webpack plugin.

## Caveats

### Scoped Style

`@media` directive with scoped style can **only work** with `css` `postcss` `scss` but not `sass`, `less` nor `stylus`

## Credits

- Windy team
- [@antfu](https://github.com/antfu) Based on his Rollup / Vite implementation & his util package


## License

MIT License © 2021 [Harlan Wilton](https://github.com/loonpwn)

