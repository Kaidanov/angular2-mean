# angular2-mean

First Command Line run to run node.js server
Each change needs to restart
```
npm run build  
```

Second Command Line to run the angular client ( views of node for now)
```
npm start
```

To use MongoDB after installation add packages
```
	Ø npm install --save mongoose
	Ø npm install mongoose-unique-validator   (--this one is for unique fields)
```

For running MongoDB server
```
E:\MongoDB\Server\3.2\bin>mongodb.exe --dbpath "e:\mongodb\db db data"
```

You can also see the port the mongo is working on and init in node.js accordingly 
//connecting to mongodb
//from running server gather the port
//creating the db if not existing
```javascript
mongoose.connect('localhost:27017/node-angular');
```

For running MongoDB client ( just to check the validity of our data - usually will be accessed trhoough the node.js code)
```
E:\MongoDB\Server\3.2\bin>mongo.exe 
```
Can check through the client using those commands :
```
	Ø use node-angular  //swithes to dn node-angular
	Ø show collections //instead of tables
	Ø db.messages.find() //gets the data of the tables/collections
```

Example of getting data from MongDB in Node.js 

..\routes\app.js
```javascript
router.get('/', function (req, res, next) {
    User.findOne({}, function(err, doc){
       if(err)
       {
           return res.send('Error!');
       }
       res.render('node', {email: doc.email});
    });
```
});
