npm init
npm install



// NOTE: The db does not exist until you create a collection.
use lessondb
// Show the current db by running db.
// Insert data into the lessondb database with this command.
// NOTE: This will create the collection automatically,
// ALSO, TAKE NOTE: the contents of the insert are basically a JS object,
// and include an array.
db.places.insert({"continent": "Africa", "country":"Morocco", "majorcities": ["Casablanca", "Fez", "Marrakech"]})
// Find all data in a Collection with db.[COLLECTION_NAME].find()
db.places.find().pretty()
// Find specific data by matching a field.
db.places.find({"continent": "Africa"})
db.places.find({"country": "Morocco"})
// Find specific data by matching an _id.
db.places.find({_id:[COPY AN OBJECTID FROM THE PREVIOUS FIND RESULTS]})
// Example: db.places.find({_id: ObjectId("5416fe1d94bcf86cd785439036")})
// Show how to update data
// using db.[COLLECTION_NAME].update()

db.places.update({"country": "Morocco"}, {$set: {"continent":"Antarctica"}})
// Note that the above will only update the first entry it matches.

// To update multiple entries, you need to add {multi:true}
db.places.update({"country": "Morocco"}, {$set: {"continent":"Antarctica"}}, {multi:true})

// Ask the class what they think will happen when you run this command,
// even though a capital doesn't exist
db.places.update({"country": "Morocco"}, {$set: {"capital":"Rabat"}})
// answer: it will create the field

// And show the field can now be updated with the same command
db.places.update({"country": "Morocco"}, {$set: {"capital":"RABAT"}})

// Show how to push to an array with $push
db.places.update({"country": "Morocco"}, {$push: {"majorcities":"Agadir"}})

// Show how to delete an entry with db.[COLLECTION_NAME].remove()
db.places.remove({"country":"Morocco"})

// Show how to empty a collection with db.[COLLECTION_NAME].remove()
db.places.remove({})

// Show how to drop a collection with db.[COLLECTION_NAME].drop()
db.places.drop()

// Show how to drop a database
db.dropDatabase()

