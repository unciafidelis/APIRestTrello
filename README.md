# APIRestTrello
An API rest for Trello

#### Process

1.  Start node project `npm init -y`
2. Install dotenv `npm install dotenv --save`
3. Create app.js

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

```javascript
KEY="TrelloKeyHere"
TOKEN="Trellotokenhere"
```
5. Install trello `npm install trello --save`

## Documentation of trello repo 

 [norberteder trello github repo](https://github.com/norberteder/trello)

