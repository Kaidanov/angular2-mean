# angular2-mean

First Command Line run to run node.js server
Each change needs to restart
```
npm run build  
```
If we want to run it for production: AoT - Ahead of time
```
npm run build:prod
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
cd E:\MongoDB\Server\3.2\bin
E:\MongoDB\Server\3.2\bin>mongod.exe --dbpath "e:\data\db"
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
cd E:\MongoDB\Server\3.2\bin
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
});
```


**_Angular2_**  
**1.Property Binding**   
Connecting to  
- DOM Properties (e.g. value, hidden)
- Directive Properties (e.g. ngStyle
- Component Properties
```
 [property] = "expression"
```
For instance 
``` 
  in Typescript
  @Input('Alias') propertyName
  
  In HTML
  <my-component [propertyName] = "expression"> </my-component>
```

**2.Event Binding**  
Connecting to   
- User/DOM events (e.g. click, mouseover..)
- Directive Events
- Components Events
```
 (event) = "expression"
```
For Instance
``` 
  in Typescript
  @Output('Alias') eventName
  
  In HTML
  <my-component (eventName) = "expression"> </my-component>
```

Directives use 'selector' to let Angular2 know which parts of the HTMLl code represent instructions
like ``*ngIf``` or  ```my-component```
``` HTML
<section  *ngIf = "condition">
<h1> Hi </h1>
</section>

<my-component> </my-component>
```


**Creating dynamic color toggle **  
In the compnenet define a member color with initial color
and at the html add this
``` HTML
<article class="panel panel-default" [ngStyle]="{backgroundColor:color}" (mouseenter)="color = 'green'" (mouseleave)="color = 'red'">
</article>
```

[ngStyle] - gives to backgroundColor the initialized value of the member of the component named color  
(mouseenter) (mouseleave) - events changing the color by event and therefore updating the backgroundColor  


** Set value reference to local control and pass it to a function back to Component **
#input is sending it's value from html to onSave function without extra parameters. 
``` Html
<div class="col-md-8 col-md-offset-2">
    <div class="form-group">
        <label for="content" >
            <input type="text" id="content" class="form-control" #input>
        </label>
    </div>
    <button class="btn btn-primary" type="submit" (click)="onSave(input.value)">Save</button>
</div>
```
In TS we know what we are waiting for - value of type string. 
``` Javascript
import {Component} from "@angular/core";
/**
 * Created by Tzvika on 11/21/2016.
 */
@Component({
    selector: 'app-message-input',
    templateUrl : './message-input.component.html'
})
export class MessageInputComponent{
    onSave(value:string){
       console.log(value);
   }
}
```


** Services **
Used for reuse in different components.
We can provide service on the app level or more specificaly per component when needed.


** NgModule **
https://angular.io/docs/ts/latest/guide/ngmodule.html

