-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 1
# Getting Started

## 01 Course Introduction
## 02 What is Angular
## 03 Angular vs Angular 2 vs Angular 6
## 04 CLI deep dive and troubleshooting
## 05 Project setup and first app
## 06 Editing the First App
## 07 The Course structure
## 08 How to get the most out of this course

## 09 What is typeescript
	Superset to js
	classes interfaces
	strong typing
	compiled to js by CLI
	pick up along the way
	addition to js not replacement

## 10 A basic project setup using  Bootstrap for styling
	ng new mark100
	npm i --save bootstrap@3
	angular.json 				->> "styles": ["node_modules/bootstrap/dist/css/bootstrap.min.css",...]

## 11 Source Code

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 2
# The Basics

## 12 Module Introduction
	what happens behind the scene?

## 13 How Angular App get loaded and started
	index.html
	app-root component created by angular for us
	Inspect the served page and see the couple of scripts inject by CLI automatically
	creating js script bundles

	main.ts is the actual entry point
	app.module.ts  bootstrap : [] list components which should be known to angular at the time po point of anaysing index.html 

	THUS
	main.ts -> app.module.ts bootstraps and make it able to handle index.html

## 14 Components are important
	Angular in the end is a js framework changing the DOM(HTML) at runtime.

	app.component -> root component
	build components having their own template code styling etc
	breakdown complex parts into reusable parts

## 15 Creating a new component
ng g c server/server
		Component is just a ts class to instatntiate objects for the CLI t orender the views
		decorators - enhance the classes, elements etc.
		metadata object in decorator - selector - to make use the html tag - unique_selector!!
									 - templateUrl: '' // a single tempate to assign the component

## 16 Understanding the role of AppModule and Component declaration
	Components to build web pages AND modules to bundle diff pieces like components into packages

## 17 Using custom components
	Include other components tag in app.component

## 18 Creating components with CLI and nesting components
	ng generate component <path/name>

## 19 Working with component templates
	Instead of external temlate can also use inline
	template: `dfv fsd sef sdf`,
	Depends on code size Decide your limit

## 20 Working with component styles
	styleUrls: []			Array of multiple ref style sheets
	styles: [` ...  `]

## 21 Fully understanding  the Component selector
	Type of selectors
						component 							template
					selector: 'app-server'					<app-server>			// css selector kind
					selector: [app-server]					<div app-server> </div> // attribute selector
					selector: '.app-server'                 <div class="app-server"> </div>																				 // by Class

##  Assignment: Practising components

## 22 What is databinding
	Communication between 
	(Typescript code Biz logic)            AND                  template(HTML)
									output data\
							String interpolation  ||  {{ data }}
							Property binding      ||  [property]="data"
									React to (User) events
							Event binding         ||  (event)="expression"

							Communication of both Two way Data Binding
									[ngModel] = "data"

## 23 String Interpolation
	{{ value }} 
	{{ 'a string' }}
	{{ 2+3 }}
	{{ functionFoo() }}
	any expression resulting into string is only condition for string interpolation syntax

## 24 Property Binding
	eg property binding to an attribute
	<button [disabled]="callTheExpression"> Add </button>	

## 25 Property Binding vs String Interpolation
	<p> {{ value }} </p>
	<p [innerText]="value"> </p>

	String interpolation - output something into template
	Property binding     - change property

##26 Event Binding
	(click) = "function()"
	(dblclick) = "expression"

## 27 Google
	<ELEMENT> properties
	<ELEMENT> events

## 28 Passing and using Data with Event Binding
	$event -- reserved variable name / data emitted with that event

	template				(input)="foo($event)"
	component				(<HTMLInputElement>event.target).value

## 29 Important!! FormsModule is require for two way data binding
	To utilize ngModel you need FormsModule

	import { FormsModule } from '@angular/forms';
	imports[ FormsModule ];

## 30 Two Way Data Binding  		
	app.module.ts
			import { FormsModule } from '@angular/forms';
			imports: [FormsModule,..];

			[(ngModel)]="data"

## 31  Combining all forms of Data Binding


## 32 Understanding Directives
		Directives - Instruction in DOM _  like components are directives with template

		<p appTrunGreen> Receives a green background </p>

		@Directive({
			selector:'[appTurnGreen]'
		})
		export class TurnGreenDirective{
			...
		}

## 33 Using ngIf to Output Data conditionally
		*ngIf="expression resulting to boolean value"				// * structural directive
		Add and remove DOM element NOT hid.e

		Structural directive				// https://angular.io/guide/structural-directives
		*ngIf *ngFor AND NGSwitch 	

## 34 Enhance ngIf with an Else condition
		#local reference	
		<button (click)="toggleMe()"> Toggle </button>
        <p *ngIf="flag1; else flag2"> Heads </p>
        <ng-template #flag2> <p> Tails </p> </ng-template>

		  toggleMe(){
   						 //this.flag1 == true ? this.flag1 = false : this.flag1 = true;
   						 this.flag1 = Math.random() > 0.5 ? true: false;
  					}

## 35 Styling elements dynamically with ngStyle
		ngStyle 			attribute directive			// https://angular.io/guide/attribute-directives
		[ngStyle]="{'background-color':'red'}"
		[ngStyle]="{backgroundColor:getColor()}"

## 36 Applyiing CSS classes dynamically
		template	 -			[ngClass]={'style-name': condition};
		component ts -			style: '.style-name{ ... }'

## 37 Outputing lists with ngFor
		*ngFor="let member of members"
				{{member}}

## 38 Getting the index using ngFor
		index

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 3
# Course Project - The Basics

## 39 Course Project
## 40 Planning the App
		layout the structure of app
		decide components
		Shopping List 	AND 	Recipe Book

## 41 Installing Bootstrap correctly
		npm i --save bootstrap@3
			old CLI  versions	angular-cli.json
			new CLI6 version 	angular.json
													styles: [node_modules/bootstrap/dist/css/bootstrap.min.css]

## 42 Get started

## 43 Creating the components
		ng g c recipes --specs false

## 44 Adding a nav bar
## 45 Alternative non collapsible navigation bar
## 46 Creating a recipe model
		with constructor
## 47 Adding content to the recipe model
## 48 Outputting a list of recipes with ngFor
## 49 Displaying recipe details
## 50 Displaying recipe details
## 51 Working with ShoppingList
## 52 Creating ingrdients Model
## 53 Creating and outputting the Shopping List
## 54 Adding a shopping List edit section
## 55 Wrap up and next step

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 4
# Debugging

## 56 Understanding Angular rror messages
		console 
## 57 Debugging code in the browser using SourceMaps
		editor > sources > webpack > . > src > app > go onnnnnnn
		source map files allowed browser to translate js in to ts or simply map our js code to ts file
## 58 Using Augury to Dive into Angular Apps
		chrome extension
-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 5
# Components and DataBinding Deep dive

## 59 Module Introduction
## 60 Splitting app into components
## 61 Property and Event Binding Overview
## 62 Binding to Custom Properties
## 63 Assigning an alias to Custom Properties
## 64 Binding to custom events
## 65 Assigning an alias to Custom Events
## 66 Custom Property and Event Binding Summary
## 67 Understanding View Ebcapsulation
## 68 More on View Encapsulation
## 69 Using local references in Templates
## 70 Getting access to the template and DOM with @ViewChild
## 71 Projecting Content into Components with ng-content
## 72 Understanding the component lifecycle
## 73 Seeing Lifecycle hooks in Action
## 74 Lifecycle hooks and Template access
## 75 Getting access to ng-content with @ContentChild
## 76 Wrap up

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 6
# Course Project - Components and Databinding


## 77 Introduction
## 78 Adding navigation with Event Binding and ngIf
## 79 Passing recipe data with Property binding
## 80 Passing Data with events and property binding ( combined )
## 81 Make sure you have FormsModule added!
## 82 Allowing the user to add ingrendients to the shopping list


-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 7
# Directives Deep Dive

## 83 Module Introduction
## 84 ngFor and ngIf Recap
## 85 ngClass and ngStyle recap
## 86 Creating a basic Attribute directive
## 87 Using  a renderer to build a Better Attribute Directive
## 88 More about renderer
## 89 Using HostListener to Listen to Host Events
## 90 Using HostBinding to Bind to Host Properties
## 91 Binding to Directive Properties
## 92 What happens behind the Scenes on Structural directives
## 93 Building a structural directive
## 94 Understanding ngSwitch

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 8
# Course Project - Directives

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 9
# Using Services and Dependency Injection

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 10
# Course Project - Using Services and Dependency Injection

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 11
# Changing Pages with Routing

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 12
# Course Project - Routing

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 13
# Understanding observables

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 14
# Course Project - Observables

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 15
# Handling Forms in Angular Apps

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 16
# Course Project - Forms

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 17
# UsingPipes to Transform Output

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 18
# Making Http Request

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 19
# Course Project - Http

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 20
# Authentication and Route Protection in Angular Apps

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 21
# Using Angular Modules and Optimising Apps

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 22
# Deploying an Angular App

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 23
# The HttpClient

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 24
# Working with NgRx in the Project

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 25
# Angular Universal

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 26
# Angular Animations

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 27
# Adding offline capabilities with Service Workers

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 28
# A basic introduction to Unit Testing in Angular Apps

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 29
# Course Roundup

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 30
# Angular 6 Changes and New Features

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 31
# Custom Project and Workflow setup

-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Section 32
# Typescript Introduction

## 412 Introduction
## 413 Using Types
## 414 Classes
## 415 Interfaces
## 416 Generics
## 417 Wrap up and Modules
## 418 Deep dive into typescript
-----------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------
# Just remeber ;) 

		|| People don’t know what they want until you show it to them.
		|| Perhaps it is good to have a beautiful mind, but an even greater gift is to discover 
		   a beautiful heart.
		|| Even a broken clock is right, twice a day.
		|| The world is your oyster. Its upto you to find the Pearls.
		|| It doesn't matter what we want, once we get it, then we want something else.
		|| A wise man can learn more from his enemies than a fool from his friends.
		|| The greatest enemy of knowledge is not ignorance, it is the illusion of knowledge.
		|| When you are dead, you do not know you are dead. It's only painful and difficult
		   for others. The same applies when you are stupid.
		|| I asked God for a bike, but I know God doesnt work that way. So I stole a bike and
		   asked for forgiveness.
		|| The soul usually knows what to do to heal itself. The challenge is to silence the mind.
		|| 
