Description
===========
node-env-configuration is a node.js module that helps with loading configuration as suggested by twelve factor methodology www.12factor.net:

```
**The twelve-factor app stores config in environment variables** (often shortened to env vars or env). Env vars are easy to change between deploys without changing any code; unlike config files, there is little chance of them being checked into the code repo accidentally; and unlike custom config files, or other config mechanisms such as Java System Properties, they are a language- and OS-agnostic standard.
…
In a twelve-factor app, env vars are granular controls, each fully orthogonal to other env vars. They are never grouped together as “environments,” but instead are independently managed for each deploy. This is a model that scales up smoothly as the app naturally expands into more deploys over its lifetime.```

Usage
=====
If you want to read into an object all env vars starting by **APP_NAME_** :
```javascript
var config = require('node-env-configuration')('appName');
```

Example
=======
Suppose you have this config. env vars:

```shell
APP_NAME_VAR1 = 'var 1';
APP_NAME_VAR2 = 'var 2';
APP_NAME_OBJ1_VAR1 = 'Obj 1 var 1';
APP_NAME_OBJ1_VAR2 = 'Obj 1 var 2';
APP_NAME_OBJ1_OBJ11_VAR1 = 'Obj 11 var 1';
```

```javascript
var config = require('node-env-configuration')('appName');
```

You'll get an object like this:

```javascript
{
    var1: 'var 1',
    var2: 'var 2',
    obj1: {
        var1: 'Obj 1 var 1',
        var2: 'Obj 1 var 2',
        obj11: {
            var1: 'Obj 11 var 1'
        }
    }
}
```
TODO
====
* Add Array support