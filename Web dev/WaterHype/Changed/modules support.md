Only one word to describe this _painful_

but after that I successfully hook node modules to client using webpack

# 1. Reading document
_pain but ok_

After reading the document about webpack I finally make my own config.js file as follow:

```js
module.exports = {
  // Entry point for client-side code
  entry,
  // Output configuration
  output: {
    filename: '[name].js',
    path: path.resolve(__dirname, 'dist'), // Output directory
  },
  // Module loaders for handling different file types
  module: {
    rules: [
      {
        test: /\.m?js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-react', '@babel/preset-env'],
            plugins: ['@babel/plugin-transform-runtime'],
          },
        },
      },
    ],
  },
  // Development mode for faster builds and debugging (optional)
  mode: 'development',
  // Enable source maps for debugging (optional)
  // devtool: 'inline-source-map',
};
```

_also not that pain_
# 2. implement it
_painful-ish part_

After an hour of hour of debugging
Im found that

[request] -> [handler] -> [complier] -> [bundle (async)] -> [sendclient] -> [take the bundle]

but the thing is the next request;

[handler] -> [compiler] -> [bundle [new]] -> [sendclient] -> [the client take the bundle [old]]

because of not using `await` in the code that make the `bundle` file desync. Client take the old `bundle` and the server just built the new one!
lol