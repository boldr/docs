# .boldrrc

Copy the `boldrrc.example` file or create a new file named `.boldrrc`

The `.boldrrc` file works similar to the `dotenv` package. Values placed in the rc should not be committed to your repository. These values will overwrite anything within the default `boldr.js` file so long as they match the naming scheme. 

**It is important to note, environmental variables take priority over your rc file**. 

For example:

`BOLDR__SERVER_PORT=3002 boldr-dx dev`

if in your `boldr.js` file, everything is the default \(3000 for port\) and your `.boldrrc` file has the port set to 3001, the value entered with the command will take precedence.



Boldr Config crawls multiple paths searching for configuration files. Once found, the values are merged based on a hierarchy \(explained below\), placed into a single object, and loaded into your application.

1. argv flags passed through the command line.
   `--db--host value`
   translates to
   `config.db.host === 'value'`
2. Environment variables defined as
   BOLDR`__DB__HOST_NAME=value`
   translates to
   `config.db.hostName === 'value'`
   **Anything below can be json5 or yaml**
   \(requires installing js-yaml\)
3. ./.boldrrc
4. ../.boldrrc
5. ../../.boldrrc
6. ...

## 

  


