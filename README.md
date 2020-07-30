# MongoDB_queries
MongoDB queries to remember

##**Basic Command**
*************
use amazon 			//create a data base
show dbs 			//show selected database
db.dropDatabase()	//delet database

db.createCollection("products")	
	//collection is create when using db.products.insertOne()

show collections 
	// show collection

db.products.insert({"name" : "macbook pro"})
	//create products collection and insert the object to the collection

db.products.drop()
	//delete products


##**CREATING QUERIES**
****************
db.products.insertOne({"name" : "macbook pro", "price" : 1500, "category" : "Computers"})
db.products.insertMany([{"name" : "iPhone 11", "price" : 900, "category" : "Electronics"}, 
							{"name" : "Headphone", "price" : 100, "category" : "Electronics"}])
	//.insertMany() argument must be an array							
							
##**FINDING QUERIES**
***************
db.products.find() 							
	//return all document in "products collection"

db.products.find().pretty()					
	//str.pretty() return formated txt as JSON(optional)

db.products.find({name : "macbook"})
	//return all product whit name

db.products.find({category : "Computers"})

db.products.find({},{"name":1})
	-> {}			// search in all data
	-> {"name":1}	// show (return) onle name

db.products.find({},{"name":1,_id:0})
	-> {"name":1}	// show (return) onle name
	-> _id=0		//don't show _id

db.products.find({},{"name":1,_id:0}).limit(2)
	-> str.limit(2) //show the two first result

db.products.find({price : {$lt: 150} })
db.products.find({price : {$lte: 100} })
db.products.find({price : {$gt: 800} })
db.products.find({price : {$gte: 900} })

db.products.find({$and:[{price : {$lt: 200} },{category: "Electronics"}]})
db.products.find({$or:[{price : {$gt: 500} },{category: "Electronics"}]})


##**UPDATE QUERIES**
**************
db.products.updateOne({name: "macbook pro"},{$set: {price: 1600} })
db.products.updateOne({name: "macbook pro"},{$set: {company: "Apple"} })
db.products.updateMany({category: "Electronics"},{$set: {category: "Electronic"} })


##**DELETEING QUERIES**
*****************
db.products.remove({name: "iPhone 11"})
db.products.deleteMany({price : {$lt: 250} })
