---
layout: post
title: Bookshelf.js Example
date: 2014-04-06
---

So getting up and running with [Bookshelf.js](http://bookshelfjs.org/) was not as easy as I was expecting.  I knew that it sits on top of [Knex.js](http://knexjs.org/) so I kept going thru the docs looking for the Bookshelf method that abstracts away table creation from Knex.  When I didn't find it, I assumed they must be doing some next level stuff where they just fully abstract away table creation/alteration on the fly.  Nope.  The answer is you just use knex for that:

Connect to your database - [Bookshelf.initialize](http://bookshelfjs.org/#Initialize)

	var Bookshelf = require('bookshelf')
	Bookshelf.conn = Bookshelf.initialize({
	    client: 'sqlite3',
	    connection: {
	        filename: './mydb.sqlite'
	    }
	})

Create your table (with knex) - [Bookshelf.knex](http://bookshelfjs.org/#Bookshelf-knex) / [knex.schema.createTable](http://knexjs.org/#Schema-createTable)

	Bookshelf.conn.knex.schema.createTable('customers', function (customer) {
	    customer.string('name')
	}).then(function () {
	    
Create your model - [Bookshelf.Model.extend](http://bookshelfjs.org/#Model-extend)

	    var Customer = Bookshelf.conn.Model.extend({
	      tableName: 'customers'
	    });
	    
Create your instance/row - [Bookshelf.Model.forge](http://bookshelfjs.org/#Model-forge)

	    Customer.forge({name: 'Reid Ransom'}).save().then(function() {
	        
	        // Say "hi"
	        console.log('hi')
	    });
	})

Note: It may look a little wierd the way the docs refer to `Bookshelf.Something` when in your code it's more like `Bookshelf.conn.Something` but they explain that under the [Bookshelf.initialize](http://bookshelfjs.org/#Initialize) docs.
