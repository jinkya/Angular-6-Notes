
---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 1
## Getting Started

### 01 Course Introduction
	...
### 02 What is Angular
	Reactive Single Page Applications (SPA) Javascript Framework
### 03 Angular vs Angular 2 vs Angular 6
	Angular 6						Angular 1
	Angular 5						|
	Angular 4               <------ complete rewrite
	Angular 2						
	Just Angular 					[ "AngularJS" ]
	Incremental improvment			Not really related to Angular 2
	No complete rewrite!

	Back in 2015/16 wa complte rewrite
	Angular js was the first framework to really make SPA and better way of maniulating DOM
	Angular 2 was complete rewrite to fix many of angular problems mostly performance
	So ANgular 2 And higher are known as just Angular
	while Angular 1 is Angular JS
	
### 04 CLI deep dive and troubleshooting
	The Angular CLI is a tool to initialize, develop, scaffold and maintain Angular applications
	startup commands

	Recommended and best way of creting angular projects coz a bit more elaborate regarding build workflow
	couple of file need to convert before running on browser, thus optimization.
	Node js Server side language - Used behind scene to bundle and optimise the project
	NPM to manage diff dependencies the angular app has.
	Download latest version - Installer
	npm install -g @angular/cli 		// mac linus prefix sudo
	download angular CLI from node pm repo
	Ignore the errors as long as successfully installed msg comes
	Create first project
	Navigate to desired folder
	ng new project_name		// dont use like test that are reserved words
	new folder with app strcuture files and dependencies and entire build workflow setup
	typescript to javascript 
	Compiled down to js by complex workflow setup
	navigate with cd
	ng serve 		// developement server localhost:4200 by default
	Boilerplate code


### 05 Project setup and first app
	Choose IDE best suits you
	VS Code, Sublime, Notepad++ or a bit adventurous simple notepad

	Code is indexing
	Might look intimidating as so many files
	Just configuration files no need to touch
	package.json	-	dependencies [dependencies_project dependencies]
						devDependencies [ reuired only for development ]
	
	<input type="text" [(ngModel)]="name">
	{{ name }} 

### 06 Editing the First App
### 07 The Course structure
### 08 How to get the most out of this course

### 09 What is typeescript
	Superset to js
	classes interfaces
	strong typing
	compiled to js by CLI
	no learning really! pick up along the way
	addition to js not replacement

### 10 A basic project setup using  Bootstrap for styling
	ng new mark100
	npm i --save bootstrap@3
	angular.json 				->> "styles": ["node_modules/bootstrap/dist/css/bootstrap.min.css",...]

### 11 Source Code

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 2
## The Basics

### 12 Module Introduction
	what happens behind the scene?

### 13 How Angular App get loaded and started
	index.html
	app-root component created by angular for us
	Inspect the served page and see the couple of scripts inject by CLI automatically
	creating js script bundles

	main.ts is the actual entry point
	app.module.ts  bootstrap : [] list components which should be known to angular at the time po point of anaysing index.html 

	THUS
	main.ts -> app.module.ts bootstraps and make it able to handle index.html
	-----------
	localhost:4200		dev server created by CLI will host our angular application
	If we change some content in app.component.html
	Its  obvious but kind of strange how does server knows to render app.component.html
	You might say this is the only component its having right now but thats not the case
	This is not the file served by the server but index.html
	This is the single page getting served
	Goto index.html _ a normal html file defined
	Body is interesting		<app-root> loading... </app-root>
	We dont see loading, somehow index.html is sseeemed to change
	app-root is not default html element instead its one of our component
	CLI creates one for us - the root component for the application
	The component which tie together our whole application in the end.

	app.component files are related to each other
	app.component.ts
		Decorator		selector: 'app-root' clear same text as index.html file
		Thisis the info angular needed to replace the index.html part with this app.component template
	content in app.component.html
	This is basically what happens at startup

	Though missing info is how angular is triggered to run over the body of index.html

	Inspect the index.html
	Couple of scripts imports at end. These are injected by CLI automatically.
	In index.html we dont have any script but whenever ng serve process rebuilds our project it will create js bundles and automatically at the scripts at the end
	A little convenient functionality for us.
	In final files script imports are present
	The first code to be executed is the code we write in main.ts
	main.ts
	Couple of imports for Some checks to check whether we are in production mode or not
	To turn of some warinning message
	Most imp is bootstrap 
	Bootstraps or starts our angular application by passing the app module to this method and app module refers to this file over here

	app.module.ts
		bootstrap: [] // Lists Components which should be known to angular at the point of time it analyzes index.html

		main.ts - bootstrap angular application and pass app.module as argument
		In app.module we tell angule hey their is this app component which you should know when startingyour application. And ang now anlyse this app.component






### 14 Components are important
	Angular in the end is a js framework changing the DOM(HTML) at runtime.

	app.component -> root component
	build components having their own template code styling etc
	breakdown complex parts into reusable parts

### 15 Creating a new component
ng g c server/server
		Component is just a ts class to instatntiate objects for the CLI t orender the views
		decorators - enhance the classes, elements etc.
		metadata object in decorator - selector - to make use the html tag - unique_selector!!
									 - templateUrl: '' // a single tempate to assign the component

### 16 Understanding the role of AppModule and Component declaration
	Components to build web pages AND modules to bundle diff pieces like components into packages

### 17 Using custom components
	Include other components tag in app.component

### 18 Creating components with CLI and nesting components
	ng generate component <path/name>

### 19 Working with component templates
	Instead of external temlate can also use inline
	template: `dfv fsd sef sdf`,
	Depends on code size Decide your limit

### 20 Working with component styles
	styleUrls: []			Array of multiple ref style sheets
	styles: [` ...  `]

### 21 Fully understanding  the Component selector
	Type of selectors
						component 							template
					selector: 'app-server'					<app-server>			// css selector kind
					selector: [app-server]					<div app-server> </div> // attribute selector
					selector: '.app-server'                 <div class="app-server"> </div>																				 // by Class

###  Assignment: Practising components

### 22 What is databinding
	Communication between 
	(Typescript code Biz logic)            AND                  template(HTML)
									output data\
							String interpolation  ||  {{ data }}
							Property binding      ||  [property]="data"
									React to (User) events
							Event binding         ||  (event)="expression"

							Communication of both Two way Data Binding
									[ngModel] = "data"

### 23 String Interpolation
	{{ value }} 
	{{ 'a string' }}
	{{ 2+3 }}
	{{ functionFoo() }}
	any expression resulting into string is only condition for string interpolation syntax

### 24 Property Binding
	eg property binding to an attribute
	<button [disabled]="callTheExpression"> Add </button>	

### 25 Property Binding vs String Interpolation
	<p> {{ value }} </p>
	<p [innerText]="value"> </p>

	String interpolation - output something into template
	Property binding     - change property

### 26 Event Binding
	(click) = "function()"
	(dblclick) = "expression"

### 27 Google
	<ELEMENT> properties
	<ELEMENT> events

### 28 Passing and using Data with Event Binding
	$event -- reserved variable name / data emitted with that event

	template				(input)="foo($event)"
	component				(<HTMLInputElement>event.target).value

### 29 Important!! FormsModule is require for two way data binding
	To utilize ngModel you need FormsModule

	import { FormsModule } from '@angular/forms';
	imports[ FormsModule ];

### 30 Two Way Data Binding  		
	app.module.ts
			import { FormsModule } from '@angular/forms';
			imports: [FormsModule,..];

			[(ngModel)]="data"

### 31  Combining all forms of Data Binding


### 32 Understanding Directives
		Directives - Instruction in DOM _  like components are directives with template

		<p appTrunGreen> Receives a green background </p>

		@Directive({
			selector:'[appTurnGreen]'
		})
		export class TurnGreenDirective{
			...
		}

### 33 Using ngIf to Output Data conditionally
		*ngIf="expression resulting to boolean value"				// * structural directive
		Add and remove DOM element NOT hid.e

		Structural directive				// https://angular.io/guide/structural-directives
		*ngIf *ngFor AND NGSwitch 	

### 34 Enhance ngIf with an Else condition
		#local reference	
		<button (click)="toggleMe()"> Toggle </button>
        <p *ngIf="flag1; else flag2"> Heads </p>
        <ng-template #flag2> <p> Tails </p> </ng-template>

		  toggleMe(){
   						 //this.flag1 == true ? this.flag1 = false : this.flag1 = true;
   						 this.flag1 = Math.random() > 0.5 ? true: false;
  					}

### 35 Styling elements dynamically with ngStyle
		ngStyle 			attribute directive			// https://angular.io/guide/attribute-directives
		[ngStyle]="{'background-color':'red'}"
		[ngStyle]="{backgroundColor:getColor()}"

### 36 Applyiing CSS classes dynamically
		template	 -			[ngClass]={'style-name': condition};
		component ts -			style: '.style-name{ ... }'

### 37 Outputing lists with ngFor
		*ngFor="let member of members"
				{{member}}

### 38 Getting the index using ngFor
		index reserved keyword
		*ngFor = "item of items; let i = index"

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 3
## Course Project - The Basics

### 39 Course Project
### 40 Planning the App
		layout the structure of app
		decide components
		Shopping List 	AND 	Recipe Book

### 41 Installing Bootstrap correctly
		npm i --save bootstrap@3
			old CLI  versions	angular-cli.json
			new CLI6 version 	angular.json
													styles: [node_modules/bootstrap/dist/css/bootstrap.min.css]

### 42 Get started

### 43 Creating the components
		ng g c recipes --specs false

### 44 Adding a nav bar
### 45 Alternative non collapsible navigation bar
### 46 Creating a recipe model
		with constructor
### 47 Adding content to the recipe model
### 48 Outputting a list of recipes with ngFor
### 49 Displaying recipe details
### 50 Displaying recipe details
### 51 Working with ShoppingList
### 52 Creating ingrdients Model
### 53 Creating and outputting the Shopping List
### 54 Adding a shopping List edit section
### 55 Wrap up and next step

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 4
## Debugging

### 56 Understanding Angular rror messages
		console 
### 57 Debugging code in the browser using SourceMaps
		debugger > sources > main.bundle > serach > place a break point & redirect to the ts file.
		debug editor > sources > webpack > . > src > app > go onnnnnnn
		source map files allowed browser to translate js in to ts or simply map our js code to ts file
### 58 Using Augury to Dive into Angular Apps
		chrome extension
---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 5
## Components and DataBinding Deep dive

### 59 Module Introduction
	...
### 60 Splitting app into components
	Split your app into multiple components according to the modularity.
### 61 Property and Event Binding Overview
	eg_ (click) [disabled] $event
	HTML Elements					Directives						Components
	Native property and Events		Custom properties and events	Custom properties and events
### 62 Binding to Custom Properties
	Parent component to child component
	<child-component-tag [childElement]="parentElement"> </child-component-tag>
	@Input() childElement;
### 63 Assigning an alias to Custom Properties
	<child-component-tag [srvElement]="parentElement"> </child-component-tag>
	@Input('srvElement') childElement;
### 64 Binding to custom events
	Getting data from child component via event

	Parent component template
				<child-component (childEmitterOne)="parentFunctionOne($event)"> </child-component>
				
	Parent component ts
								  parentFunctionOne(someData) { }
	Child component template
								<button (click)="childFunctionOne()"> Add </button>
	Child component ts
								 @Output() childEmitterOne  = new EventEmitter<someData>();

								    childFunctionOne(){
    												this.childEmitterOne.emit(someData);
  													}

### 65 Assigning an alias to Custom Events
		@Output('someAliasname')

### 66 Custom Property and Event Binding Summary
		Approach matters
		Above @Input and @Output methods are okay for simple components data passing BUT
		If components are related in a far distance use Services.
		Its not like services are better than the above approach but things get simpliefied. 
### 67 Understanding View Ebcapsulation
	eg._ Angular enforces style encapsulation ( Each component, each style like )
	Shadow DOM
### 68 More on View Encapsulation
	import { ViewEncapsulation } from '@angular/core';
	@Component({
		...
		encapsulation: ViewEncapsulation.Emulated		// Native, None, Emulated(Default)
	})
### 69 Using local references in Templates
	Refers to the whole HTML element its present on.
	Template
			<input type="text" #refer>
			<button (click)="funA(refer)"> </button>
	Component
			funA(data){ data.value }
### 70 Getting access to the template and DOM with @ViewChild
	Get access of DOM inside ts
	Template
			<input type="text" class="form-control" #serverContentInput>
	Component ts
			 @ViewChild('serverContentInput') mySelectedElement: ElementRef;         // CockpitComponent
			 ( this.mySelectedElement.nativeElement.textContent ) to access the text value of the HTML element

### 71 Projecting Content into Components with ng-content
	Passing HTML to pass into component from outside
	explore more example...
### 72 Understanding the component lifecycle
	Lifecycle
		ngOnChnages					Called after a bound input property changes
		ngOnInit					Called once the component initialised
		ngDoCheck					Called during every change detection run
		ngAfterContentInit			Called after content (ng-content) has been projected into view
		ngAfterContentChecked		Called every time the projected content has been checked
		ngAfterViewInit				Called after the components view (and childviews) has been initialised
		 ngAfterViewChecked			Called every time the view (and childviews) has been checked
		 ngOnDestroy				Called once the component is about to be destroyed
### 73 Seeing Lifecycle hooks in Action
### 74 Lifecycle hooks and Template access
### 75 Getting access to ng-content with @ContentChild

### 76 Wrap up

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 6
## Course Project - Components and Databinding


### 77 Introduction
### 78 Adding navigation with Event Binding and ngIf
### 79 Passing recipe data with Property binding
### 80 Passing Data with events and property binding ( combined )
### 81 Make sure you have FormsModule added!
### 82 Allowing the user to add ingrendients to the shopping list


---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 7
## Directives Deep Dive

### 83 Module Introduction
			Directives - 		
		Attribute 						  AND 	    Structural
		Looks like normal HTML attribute.			Looks like normal HTML attribute but with a leading *.
		Only affect/change the element they			Affect the whole area in DOM
		are added to.								( elements get added or removed )
### 84 ngFor and ngIf Recap
				Two structural directives can't be assigned to a single HTMLDOM element.
				*ngFor="let item of items"
				*ngIf = "conditionExpression"
### 85 ngClass and ngStyle recap
						[ngClass]="{cssClass: booleanExpressionValue}"
						[ngStyle]="{backgroundColor: expression ? 'yellow':'transparent'}"
						[ngStyle]="{"background-color": expression ? 'yellow':'red'}"
### 86 Creating a basic Attribute directive
				basic-highlight.directive.ts
						import { Diective, ElementRef, OnInit } from '@angular/core';
						@Directive({
								selector: '[appBasicHighlight]'
							})
						export class BasicHighlightDirective implements onInit{
								constructor(private elementRef: ElementRef) {}
								ngOnInit(){
									this.elementRef.nativeElement.style.backgroundColor = 'green';
								}
						}
				app.module.ts
						import { BasicHighlightDirective } from './path/basic-highlight.diective';
						declarations: [..., BasicHighlightDirective]
				template
						<p appBasicHighlight> Style with appBasicHighlight directive </p>
### 87 Using  a renderer to build a Better Attribute Directive
				ng g d better-highlight
				better-highlight.directive.ts
					import { Directive, OnInit, Renderer2, ElementRef } from '@angular/core';
					@Directive({
						selector: '[appBetterHighlight]'		
					})
					export class BetterHighlightDirective{
						constructor( private elRef: ElementRef, private renderer: Renderer ){}
						ngOnInit(){
								this.renderer.style(this.elRef.nativeElement, 'bakcground-color','blue');
								}
					}
				template
						<p appBetterHighlight> Style with appBasicHighlight directive </p>
				Angular is not limited to unning into browser, also works with service workers like 			  
				environments where DOM access is not provided.
				Preference should be to Renderer for DOM Mapnipulation.
				Official doc[https://angular.io/api/core/Renderer2]
### 88 More about renderer
### 89 Using HostListener to Listen to Host Events
### 90 Using HostBinding to Bind to Host Properties
### 91 Binding to Directive Properties
### 92 What happens behind the Scenes on Structural directives
### 93 Building a structural directive
### 94 Understanding ngSwitch

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 8
## Course Project - Directives

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 9
## Using Services and Dependency Injection

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 10
## Course Project - Using Services and Dependency Injection

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 11
## Changing Pages with Routing
	Multiple pages URL changing and still using single page

### Module Introduction
### Why do we need a router
	separate pages
### Understanding the example project
	explore the route -start
### Seting up and Loading routes
	app.module.ts
		import { Routes, RouterModule } from "@angular/router";
		const appRoutes: Routes = [
			{ path: '', component: HomeComponent },			// dont add the slash
			{ path: 'users', component: UserComponent },
			{ path: 'servers', component: ServerComponent },
		];
		// Register these routes in app
		imports: [
			...,
			RouteModule.forRoot(appRoutes)
		]

	Add a special directive to template
			<router-outlet> </router-outlet>

### Navigating with Router Links
	Whats wrong with href="/" or href="/home", it reloads/ refreshes the app and
	we are building a SPA.
	Application state lossed due to this
	Special attribute by Angular
	routerLink="/"
	routerLink="/servers"
	[routerLink] = "['/users','suffix1']"
	Its faster than reloading the page

### Understandiing navigation path
	routerLink inside another routerLink
	give absoulte path pr relative path accordingly
### Styling Active Router Links
	Styling active tab
	routerLinkActive="active"
	[routerLinkActiveOptions] = "{exact:true}"		// for base link to remove the css
### Navigating Programmatically
	event navigation
		template
			<button class="btn btn-primary" (click)="onLoadServers()"> Load servers </button>
		ts file
			import { Router } from '@angular/router';
			constructor(private router:Router) { }
			onLoadServers(){
   					 	//complex calculations and
    					this.router.navigate(['/servers']);
  					}
### Using relative paths in Programmatic Navigation
	Unline routerLink, router.navigate() does not know on which route you are currently on so.
	thus
		template
			<button class="btn btn-primary" (click)="onReload()"> Reload Page </button>
		ts file
			import { Router, ActivatedRoute } from '@angular/router';
			constructor(private router:Router, private route: ActivatedRoute) { }
			  onReload(){
      						this.router.navigate(['servers'], {relativeTo: this.route});
  						}
### Passing Parameters to Routes
	{ path: 'users/:id',  component: UserComponent }, // parameteres dynamic segments
### Fetching Route Parameters
	app.module.ts
		{ path: 'users/:id/:name',  component: UserComponent }, // parameteres dynamic segments
	template
		{{user.id}} AND {{user.name}}
	ts
		import { ActivatedRoute } from '@angular/router';
		constructor(private route:ActivatedRoute) { }
		
		id: this.route.snapshot.params['id'],
        name: this.route.snapshot.params['name']

### Fetching Route Parameters Relatively
	Retrieving route parameters can fail in some cases
	Like
		template
			user.component.ts				// localhost:4200/users/1/ajinkya
				<p>{{ user.id }}</p>		// 1
				<p>{{user.name}}</p>		// ajinkya
				<hr>
				<a [routerLink]="['/users', 10, 'Ana']"> Load Ana id 10 </a>
			ts
				import { ActivatedRoute, Params } from '@angular/router';
				  ngOnInit() {
   							 this.user = { 
   							   id: this.route.snapshot.params['id'],
   							   name: this.route.snapshot.params['name']
   							  };
   							  this.route.params          // param_ observable for async task
   							  .subscribe(
   							    (params: Params) => {
   							      this.user.id = params['id'];
   							      this.user.name = params['name'];
   							    } 
   							  );
 							 }

### An important note about Route Observables
	Not necessary but sometimes observable is required to be killed.
		ts file
			import { Component, OnInit, OnDestroy } from '@angular/core';
			import { ActivatedRoute, Params } from '@angular/router';
			import { Subscription } from 'rxjs/Subscription';
			
			paramsSubscription: Subscription;
			ngOnInit() {
			    this.user = { 
			      id: this.route.snapshot.params['id'],
			      name: this.route.snapshot.params['name']
			     };
			      this.paramsSubscription = this.route.params          // param_ observable for async task
			     .subscribe(
			       (params: Params) => {
			         this.user.id = params['id'];
			         this.user.name = params['name'];
			       } 
			     );
			  }
			
			  ngOnDestroy(){
			    this.paramsSubscription.unsubscribe();
			  }
### Passing Query Parameters and Fragments
	        [routerLink]="['/servers',5,'edit']"
        	[queryParams]="{allowEdit:'1'}"
        	fragment="loading"

			/servers/5/edit?allowEdit=1#loading
### Retrieving Query Parameters and Fragments
### practising and some common gotchas
### Setting up Child (Nested) Routes
### Using Query Parameters - Practise
### Configuring the handeling of Query Parameters
### Redirecting and Wildcard routes
	[
		{ path: 'not-found', component: pageNotFound },
		{ path: '**', redirectTo: 'not-found'}
	]
### Important: Redirection Path matching
	pathMatch: 'full'
### Outsourcing the Route configuration

### An introduction to guards
	to authenticate routes
### Protecting routes with canActivate
	canActivate in path and write and auth guard with Auth Service
	

### Protecting child (Nested) routes with canActivate
### Using a Fake Auth service
### Controlling Navigation with canDeactivate
### Passing static data to a route
### Resolving Dynamic data with the resolve Guard
### Wrap up

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 12
## Course Project - Routing

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 13
## Understanding observables

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 14
## Course Project - Observable

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 15
## Handling Forms in Angular Apps

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 16
## Course Project - Forms

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 17
## Using Pipes to Transform Output
	Transform output into your template
	eg_ username = "Ajinkya"	<p> {{ username | uppercase }} </p> => AJINKYA		 || inbuilt pipe
	    started: new Date(15, 1, 2017)		<p> {{ started }} </p>					 || Mon Aug 09 1920 00:00:00 GMT+0530 
																					    (India Standard Time)
											<p> {{ started | date }} </p>			 || Aug 9, 1920
											<p> {{ started | date:'fullDate' }} </p> || Monday, August 9, 1920


### Introduction and why pipes are useful
### Using pipes
### Parametrizing pipes
	<p> {{ started | date:'fullDate' }} </p> || Monday, August 9, 1920

### Where to learn more about pipes
https://angular.io/api?query=pipe

### Chaining multiple pipes
! CAUTION order is important
generally parsed from left to right
{{ started | date:'fullDate' | uppercase }}

### Creating a custom pipe
ng generate pipe <pipe_name> --spec=false

### Parametrizing a custom pipe
component
<strong>{{ server.name | shorten:8:'hi' }}</strong>
ts
transform(value: any, limit: any, extra1?: any): any {
  console.log(limit);
  console.log(extra1);

  return value;
}

### Example : Creating a custom pipe
ts----
  servers = [
    {
      instanceType: 'medium',
      name: 'Production Server',
      status: 'stable',
      started: new Date(15, 1, 2017)
    },....
  ]

filter----
ng g p filter
  transform(value: any, filterString: string, propName: string): any {
    if(value.length === 0 || filterString === ''){
      return value;
    }
    const resultArray = [];
    for(const item of value){
      if (item[propName]===filterString){
        resultArray.push(item);
      }
    }
    return resultArray;
  }

component----
<input type="text" [(ngModel)]="filteredStatus">
*ngFor="let server of servers | filter:filteredStatus:'status'"

### Pure and impure pipes ( How to fix the "filter pipe" )
Angular do not rerun the pipe whenever filter data changes but you can change that by
pure: false;
Pipe recalculation whenever data changes but can lead to performance issues.

@Pipe({
  name: 'filter',
  pure: false
})

### Understanding the "async" pipe
ts
  appStatus = new Promise((resolve, reject)=>{
    setTimeout( ()=> { resolve('stable'); } ,2000)
  })

component
<p>App status {{ appStatus | async  }} </p>

### Assignment 8: Practising pipes
Reverse Pipe
	value.split('').reverse('').join('')
Sort Pipe
transform(value: any, propName: string) 
....
	value.sort((a,b)=>{
		if(a[propName] > b[propName]){
			return 1
		} else {
			return -1
		}
	})
---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 18
## Making Http Request

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 19
## Course Project - Http

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 20
## Authentication and Route Protection in Angular Apps

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 21
## Using Angular Modules and Optimizing Apps

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 22
## Deploying an Angular App

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 23
## The HttpClient

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 24
## Working with NgRx in the Project

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 25
## Angular Universal

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 26
## Angular Animations

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 27
## Adding offline capabilities with Service Workers

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 28
## A basic introduction to Unit Testing in Angular Apps

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 29
## Course Roundup

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 30
## Angular 6 Changes and New Features
### 396 What changed with Angular 6?
	No breaking changes in Angular 6, easily fixable
	Breaking changes introduced by its RxJS 6 Dependency.

	RxJS 6
	Observables library behind the scene like using HttpClinent
	Internal package structure changed
	-- Changed imports						-- Changed Operator Usage
					Add backward compatibility with rxjs-compat
	
### 397 A first look at angular elements
### 398 Additional resources and Articles
---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
### Section 31
### Custom Project and Workflow setup

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Section 32
## Typescript Introduction
	
### 412 Introduction
	...
### 413 Using Types
	let a: string;			  // strong type String for a
	let a = "test string";    // type infered as String thus
	a = 4;					  // error

	let a;						// declare without initializing thus type : any
	a= 'hello';
	a=4;						// no error But try to avoid this.

	Basic types
	string
	number
	boolean
	Array<string>
	any

	avoid for function OR enum CAn also create your own types

### 414 Classes
	class Car{
		engineName: string;
		gears: number;
		private speed: number;

		constructor(){
			this.speed = speed || 0;
		}
		accelerate():void{
			this.speed++;
		}
		throttle():void{
			this.speed--;
		}
		getSpeed():void{
			console.log(this.speed);
		}
		static numberOfWheels:number{
			return 4;
		}
	}

	let car = new Car(5);
	car.accelerate();
	car.getSpeed();

	console.log(Car.nuberOfWheels);		// access method without instantiating the Object
	
### 415 Interfaces
	secure form of communication

	interface User{
		username: string;
		password: string;
		confirmPassword?: string;
	}
	let user:User;
	user = {username:'ajinkya', password:'itssecret'};

	Can also contain functions
	interface CanDrive{
		accelerate(speed:number): void;
	}

	let car:CanDrive{
		accelerate: function (speed:number){
			...
		}
	}

### 416 Generics
	Allow us to be flexible regarding types of objects used
	let numberArray: Array<number>;
	numberArray = [3,7,4,5];

### 417 Wrap up and Modules
// can export class, interface, variable,...
	export class ExportedClass{
		// this class can be exported
	}
### 418 Deep dive into typescript
	Normal js can be used to write Angular apps, but its extremely hard to find the reference resources.
	www.typescriptlang.org
---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
# 7 rule to excel
		|| Take responsibility of your life.
		|| Accept failure.
		|| What you do at 8 pm matters.
		|| Success is a lonely road. Failure is crowded highway.
		|| The last 10% is hardest to finish.
		|| Know why you want it.
		|| Continuously learn.


# Just remember ;) 

		|| People donâ€™t know what they want until you show it to them.
		|| Perhaps it is good to have a beautiful mind, but an even greater gift is to discover 
		   a beautiful heart.
		|| Even a broken clock is right, twice a day.
		|| The world is your oyster. Its upto you to find the Pearls.
		|| It doesn't matter what we want, once we get it, then we want something else.
		|| A wise man can learn more from his enemies than a fool from his friends.
		|| The greatest enemy of knowledge is not ignorance, it is the illusion of knowledge.
		|| When you are dead, you do not know you are dead. It's only painful and difficult
		   for others. The same applies when you are stupid.
		|| The soul usually knows what to do to heal itself. The challenge is to silence the mind.


---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------

## NG CONF
### Lets build a form around it
	yusuf sani stackblitz

Reactive Forms

Building Blocks
FormControl			FormGroup			FormArray

Getting started
	import { ReactiveFormModule } from "@angular/forms";
	imports: [ReactiveFormModule]

FormControl
	Used to bind to individual inputs in Template

	export class MyComponent{
		public myFormControl: FormControl;

		constructor(){
			this.myFormControl = new FormControl('');
		}
	}

	<input [formControl]="myFormControl" type="text" id="my-form" name="my-form">

FormGroup
	Works maily with the HTML "Form" Element

---------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------
## Links 
[malcoded](https://malcoded.com/)
[metaltoad](https://www.metaltoad.com/blog)
[flutter location](https://pub.dartlang.org/packages/location#-readme-tab-)
[AngularFirebase](https://angularfirebase.com/)
