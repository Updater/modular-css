modular-css-webpack [![NPM Version](https://img.shields.io/npm/v/modular-css-webpack.svg)](https://www.npmjs.com/package/modular-css-webpack) [![Build Status](https://img.shields.io/travis/tivac/modular-css/master.svg)](https://travis-ci.org/tivac/modular-css)
===========
<p align="center">
    <a href="https://www.npmjs.com/package/modular-css-webpack" alt="NPM License"><img src="https://img.shields.io/npm/l/modular-css-webpack.svg" /></a>
    <a href="https://www.npmjs.com/package/modular-css-webpack" alt="NPM Downloads"><img src="https://img.shields.io/npm/dm/modular-css-webpack.svg" /></a>
</p>

`modular-css-webpack/plugin` provides a webpack 2 plugin you can use to transform imported `.css` files into lookup objects while outputting CSS to disk.

`modular-css-webpack/loader` provides the file loader that does the actual transformation on files.

You will need to use **both** in tandem for things to work!

## Usage

```js
// webpack.config.js
var path = require("path"),
    
    CSSPlugin = require("modular-css-webpack/plugin");

module.exports = {
    entry   : "./input.js",
    output  : {
        path : path.resolve(__dirname, "dist"),
        filename : "./output.js"
    },
    module : {
        rules : [
            {
                test : /\.css$/,
                use  : "modular-css-webpack/loader"
            }
        ]
    },
    plugins : [
        new CSSPlugin({
            css  : "./output.css",
            json : "./output.json"
        })
    ]
});
```

## Options

### `css`

Location to write the generated CSS file to, relative to `output.path` just like `output.filename`

### `json`

Location to write out the JSON mapping file to, relative to `output.path` just like `output.filename`

### Shared Options

All other options are passed to the underlying `Processor` instance, see [Options](https://github.com/tivac/modular-css/blob/master/docs/api.md#processor-options).
