# APIRestTrello
An API rest for Trello

#### Process

1.  Start node project `npm init -y`
2. Install dotenv `npm install dotenv --save`
3. Create app.js

#### app.js
```javascript
require('dotenv').config()

if(!process.env.TOKEN && !process.env.KEY){
  throw new Error('No hay configuración con Api Key y con Token')
}

let Trello = require("trello");
let trello = new Trello(process.env.KEY, process.env.TOKEN);

let cardTitle = `Card Nueva ${new Date()}`

trello.addCard(cardTitle, "LaunchX Card Description", "6264e42be72d295e64f5c083",
	function (error, trelloCard) {
		if (error) {
			console.log('Could not add card:', error);
		}
		else {
			console.log('Added card:', trelloCard);
		}
	});
```

4. Create a file named `.env`

#### .env

```javascript
KEY="TrelloKeyHere"
TOKEN="Trellotokenhere"
```
5. Install trello `npm install trello --save`

## Documentation of trello repo 

 [norberteder trello github repo](https://github.com/norberteder/trello)

6. Install Linter `npm install eslint --save-dev`
7. Run `npm init @eslint/config` to config linter

	- Problems
	- commonjs
	- none
	- No
	- browser
	- Javascript

8. Update file .eslintrc.js

#### .eslintrc.js

```javascript
module.exports = {
    "env": {
        "browser": true,
        "commonjs": true,
        "es2021": true,
    },
    "extends": "eslint:recommended",
    "parserOptions": {
        "ecmaVersion": "latest"
    },
    "rules": {
        indent: ["error", 4],
        "linebreak-style": ["error", "unix"],
        quotes: ["error", "double"],
        semi: ["error", "always"]
    }
};
```
9. Update package.json

#### Package.json

```javascript
{
  "name": "apiresttrello",
  "version": "1.0.0",
  "description": "An API rest for Trello",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "linter": "node ./node_modules/eslint/bin/eslint.js .",
    "linter-fix": "node ./node_modules/eslint/bin/eslint.js . --fix"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/unciafidelis/APIRestTrello.git"
  },
  "keywords": [],
  "author": "Alejandro Morgan",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/unciafidelis/APIRestTrello/issues"
  },
  "homepage": "https://github.com/unciafidelis/APIRestTrello#readme",
  "devDependencies": {
    "eslint": "^8.14.0",
    "jest": "^28.0.3"
  },
  "dependencies": {
    "dotenv": "^16.0.0",
    "node-fetch": "^3.2.4",
    "trello": "^0.11.0"
  }
}
```

10. Run linter `npm run linter`
11. Run linter fix `npm run linter-fix`

*You notice `'process' is not defined error` but it's ok, since this is a property of dotenv that carries sensitive info from .env to app.js


### Notes

Notice that `jest` and `node-fetch` were installed before the main changes as they show in `packege.json`, but were not used in this project; fell free to skip them.