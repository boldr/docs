# Boldr Configuration

The main configuration for Boldr's build system and server is located in the root of your project inside the `.boldr` folder. The file `boldr.js` contains everything you need to customize your installation.





### The Inline

```
inline: {
    SERVER_PORT: process.env.BOLDR__SERVER_PORT,
    DEV_SERVER_PORT: process.env.BOLDR__DEV_PORT,
  },
```

Inline is the first section of the config. Here are the values for your server's port and the dev server port. They are passed to the Webpack compiler and their values set at compile time.



### The Bundle

```
bundle: {
    verbose: true,
    debug: false,
    cssModules: true,
    wpProfile: false,
    webPath: '/assets/',
    publicDir: path.resolve(__dirname, '../public'),
    assetsDir:  path.resolve(__dirname, '../public/assets'),
    srcDir: path.resolve(__dirname, '../src'),
    client: {
      entry: path.resolve(__dirname, '../src/client/index.js'),
      bundleDir: path.resolve(__dirname, '../public/assets'),
    },
    server: {
      entry: path.resolve(__dirname, '../src/server/index.js'),
      bundleDir: path.resolve(__dirname, '../server'),
    },
```

Bundle is the second block of configuration. Webpack uses the values here to output your project to the correct directories. 

**verbose/debug**: Toggling to **true **or **false** controls how much output during development you will see from Webpack.

**cssModules**: Set to false, to turn off CSS modules in the Webpack config.

**wpProfile**: Collects profiling information about your bundles during production. Set the value to true,  run `boldr-dx build` and Webpack will collect data you can use to analyze the bundle.

**webPath**: This is where your assets are served from. For example boldr.io/assets/bundle.js. 



Finally, there is **vendor**. The vendor array is **extremely important.**

Every time you add or remove a third party dependency that belongs in the browser bundle, you must add that file to the vendor array. This is because not only are vendor files split into their own bundle, but mixed between chunks and a common bundle. 

```
vendor: [
      'animate-components',
      'apollo-client',
      'axios',
      'boldr-ui',
      'boldr-utils',
      ...excluded
]
```

The remaining values modify where the bundle entry and output goes.



### Server Settings

Everything below the bundle is related to the server.



```
    server: {
      port: 3000,
      host: '127.0.0.1',
      apiPrefix: '/api/v1',
      siteUrl: 'http://localhost:3000',
    },
    logging: {
      level: 'debug',
      file: {
        enable: true,
        dir: 'logs',
        level: 'info',
        filename: 'boldr.api',
      },
    },
    db: {
      url: 'postgres://postgres:password@127.0.0.1:5432/boldr',
      name: 'boldr',
      debug: false,
    },
    redis: {
      url: 'redis://127.0.0.1:6379',
    },
    token: {
      iss: 'boldr',
      aud: '',
      algorithm: 'HS256',
      secret: 'b0ldrk3kwi11s15',
    },
    mail: {
      host: 'smtp.example',
      port: 465,
      ssl: true,
      user: 'hello@boldr.io',
      password: 'password',
      from: 'hello@boldr.io',
    },
    cors: {
      whitelist: ['http://localhost:2121', 'http://localhost:3000'],
    },

```



