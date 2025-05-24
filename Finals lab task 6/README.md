use mongo_practice
switched to db mongo_practice
Insert the following documents into a `movies` collection.

db.movies.insert({title:"Fight Club", writer: "Chuck Palahniuk", year: "1999", actors:["Brad Pitt", "Edward Norton"]})
DeprecationWarning: Collection.insert() is deprecated. Use insertOne, insertMany, or bulkWrite.
{
 acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307618082aab3cd7c80c9b')
  }
}
 db.movies.insert({title:"Pulp Fiction", writer:"Quentin Tarantino", year:"2009", actors:["John Travolta", "Uma Thurman"]})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307626082aab3cd7c80c9c')
  }
}
db.movies.insert({title:"Inglorious Basterds", writer:"Quentin Tarantino", year:"2009", actors:["Brad Pitt", "Diane Kruger", "Eli Roth"]})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830762e082aab3cd7c80c9d')
  }
}
db.movies.insert({title:"The Hobbit: An unexpected Journey", writer:"J.R.R. Tolkein", year:"2012",franchise:"The Hobbit"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307635082aab3cd7c80c9e')
  }
}
db.movies.insert({title:"The Hobbit: The Desolation of Smaug", writer:"J.R.R Tolkien", year:"2013", franchise:"The Hobbit"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830763d082aab3cd7c80c9f')
  }
}
db.movies.insert({title:"The Hobbit: The Battle of the Five Armies", writer:"J.R.R Tolkien", year:"2002", franchise:"The Hobbit", synopsis:"Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('68307649082aab3cd7c80ca0')
  }
}
db.movies.insert({title:"Pee Wee Herman's Big Adventures"})
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId('6830765b082aab3cd7c80ca1')
  }
}
db.movies.insert({title:"Avatar"})
db.movies.find()
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  year: '1999',
  actors: [
    'Brad Pitt',
    'Edward Norton'
  ]
}
{
  _id: ObjectId('68307626082aab3cd7c80c9c'),
  title: 'Pulp Fiction',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'John Travolta',
    'Uma Thurman'
  ]
}
{
  _id: ObjectId('6830762e082aab3cd7c80c9d'),
  title: 'Inglorious Basterds',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'Brad Pitt',
    'Diane Kruger',
    'Eli Roth'
  ]
}
{
  _id: ObjectId('68307635082aab3cd7c80c9e'),
  title: 'The Hobbit: An unexpected Journey',
  writer: 'J.R.R. Tolkein',
  year: '2012',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('6830763d082aab3cd7c80c9f'),
  title: 'The Hobbit: The Desolation of Smaug',
  writer: 'J.R.R Tolkien',
  year: '2013',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('68307649082aab3cd7c80ca0'),
  title: 'The Hobbit: The Battle of the Five Armies',
  writer: 'J.R.R Tolkien',
  year: '2002',
  franchise: 'The Hobbit',
  synopsis: 'Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness.'
}
{
  _id: ObjectId('6830765b082aab3cd7c80ca1'),
  title: "Pee Wee Herman's Big Adventures"
}
{
  _id: ObjectId('68307663082aab3cd7c80ca2'),
  title: 'Avatar'
}
db.movies.find({writer:"Quentin Tarantino"})
{
  _id: ObjectId('68307626082aab3cd7c80c9c'),
  title: 'Pulp Fiction',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'John Travolta',
    'Uma Thurman'
  ]
}
db.movies.find({actors:"Brad Pitt"})
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  year: '1999',
  actors: [
    'Brad Pitt',
    'Edward Norton'
  ]
}
{
  _id: ObjectId('6830762e082aab3cd7c80c9d'),
  title: 'Inglorious Basterds',
  writer: 'Quentin Tarantino',
  year: '2009',
  actors: [
    'Brad Pitt',
    'Diane Kruger',
    'Eli Roth'
  ]
}
db.movies.find({franchise:"The Hobbit"})
{
  _id: ObjectId('68307635082aab3cd7c80c9e'),
  title: 'The Hobbit: An unexpected Journey',
  writer: 'J.R.R. Tolkein',
  year: '2012',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('6830763d082aab3cd7c80c9f'),
  title: 'The Hobbit: The Desolation of Smaug',
  writer: 'J.R.R Tolkien',
  year: '2013',
  franchise: 'The Hobbit'
}
{
  _id: ObjectId('68307649082aab3cd7c80ca0'),
  title: 'The Hobbit: The Battle of the Five Armies',
  writer: 'J.R.R Tolkien',
  year: '2002',
  franchise: 'The Hobbit',
  synopsis: 'Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness.'
}
db.movies.find({year:{$gt:"1990", $lt:"2000"}})
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  year: '1999',
  actors: [
    'Brad Pitt',
    'Edward Norton'
  ]
}
db.movies.find({$or:[{year:{$gt:"2010"}},{year: {$lt:"2000"}}]})
{
  _id: ObjectId('68307618082aab3cd7c80c9b'),
  title: 'Fight Club',
  writer: 'Chuck Palahniuk',
  
