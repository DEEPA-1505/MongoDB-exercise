# MongoDB-exercise

Microsoft Windows [Version 10.0.22631.5472]
(c) Microsoft Corporation. All rights reserved.


C:\Users\deepi>mongosh
Current Mongosh Log ID: 6884f379fafe312e1eeec4a8
Connecting to:          mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.5.6
Using MongoDB:          8.0.12
Using Mongosh:          2.5.6


For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/


------
   The server generated these startup warnings when booting
   2025-07-26T18:44:45.034+05:30: Access control is not enabled for the database. Read and write access to data and configuration is unrestricted
------

//creare operation

test> use library

switched to db library

library> db.library.books

library.library.books

library>  db.books.insertOne({title:"ignited minds",author:"Dr.Apj Abdul Kalam",published_year:2002})
{
  acknowledged: true,
  insertedId: ObjectId('6884f857fafe312e1eeec4a9')
}

library> db.books.find()
[
  {
    _id: ObjectId('6884f857fafe312e1eeec4a9'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002
  }
  
library> db.books.insertOne({title:"The Tata story",author:"Peter Casey",published_year:2018})
{
  acknowledged: true,
  insertedId: ObjectId('6884fa17fafe312e1eeec4aa')
}

//Read operation


library> db.books.find()
[
  {
    _id: ObjectId('6884f857fafe312e1eeec4a9'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002
  },
  {
    _id: ObjectId('6884fa17fafe312e1eeec4aa'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  }
]

library> db.books.find({author:"Peter Casey"})
[
  {
    _id: ObjectId('6884fa17fafe312e1eeec4aa'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  }
]

library> db.books.find().sort({published_year:1}).limit(1)
[
  {
    _id: ObjectId('6884f857fafe312e1eeec4a9'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002
  }
]


//update operation

library>  db.books.updateOne({title:"The Tata story"},{$set:{published_year:2025}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}

library> db.books.find()
[
  {
    _id: ObjectId('6884f857fafe312e1eeec4a9'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002
  },
  {
    _id: ObjectId('6884fa17fafe312e1eeec4aa'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2025
  }
]

library>  db.books.updateMany({},{$set:{genre:"Mystery"}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 2,
  modifiedCount: 2,
  upsertedCount: 0
}

library> db.books.find()
[
  {
    _id: ObjectId('6884f857fafe312e1eeec4a9'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002,
    genre: 'Mystery'
  },
  {
    _id: ObjectId('6884fa17fafe312e1eeec4aa'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2025,
    genre: 'Mystery'
  }
]


//Delete operation

library> db.books.deleteOne({published_year:2025})
{ acknowledged: true, deletedCount: 1 }

library> db.books.find()
[
  {
    _id: ObjectId('6884f857fafe312e1eeec4a9'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002,
    genre: 'Mystery'
  }
]

library>  db.books.insertOne({title:"The Tata story",author:"Peter Casey",published_year:2018})
{
  acknowledged: true,
  insertedId: ObjectId('68850d74fafe312e1eeec4ab')
}

library> db.books.find()
[
  {
    _id: ObjectId('6884f857fafe312e1eeec4a9'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002,
    genre: 'Mystery'
  },
  {
    _id: ObjectId('68850d74fafe312e1eeec4ab'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  }
]

library> db.books.deleteMany({published_year:{$lt:2003}})
{ acknowledged: true, deletedCount: 1 }

library> db.books.find()
[
  {
    _id: ObjectId('68850d74fafe312e1eeec4ab'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  }
]


//Advanced query

library>  db.books.insertOne({title:"ignited minds",author:"Dr.Apj Abdul Kalam",published_year:2002})
{
  acknowledged: true,
  insertedId: ObjectId('68851100fafe312e1eeec4ac')
}

library> db.books.find()
[
  {
    _id: ObjectId('68850d74fafe312e1eeec4ab'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  },
  {
    _id: ObjectId('68851100fafe312e1eeec4ac'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002
  }
]

library>  db.books.insertOne({title:"MongoDB",author:"Deepa",published_year:2025})
{
  acknowledged: true,
  insertedId: ObjectId('68851216fafe312e1eeec4ad')
}

library>  db.books.insertOne({title:"NOSQL",author:"vijay",published_year:2023})
{
  acknowledged: true,
  insertedId: ObjectId('68851251fafe312e1eeec4ae')
}

library> db.books.find()
[
  {
    _id: ObjectId('68850d74fafe312e1eeec4ab'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  },
  {
    _id: ObjectId('68851100fafe312e1eeec4ac'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002
  },
  {
    _id: ObjectId('68851216fafe312e1eeec4ad'),
    title: 'MongoDB',
    author: 'Deepa',
    published_year: 2025
  },
  {
    _id: ObjectId('68851251fafe312e1eeec4ae'),
    title: 'NOSQL',
    author: 'vijay',
    published_year: 2023
  }
]

library> db.books.find().sort({published_year:-1}).limit(3)
[
  {
    _id: ObjectId('68851216fafe312e1eeec4ad'),
    title: 'MongoDB',
    author: 'Deepa',
    published_year: 2025
  },
  {
    _id: ObjectId('68851251fafe312e1eeec4ae'),
    title: 'NOSQL',
    author: 'vijay',
    published_year: 2023
  },
  {
    _id: ObjectId('68850d74fafe312e1eeec4ab'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  }
]

library> db.books.find({title:/MongoDB|NOSQL/i})
[
  {
    _id: ObjectId('68851216fafe312e1eeec4ad'),
    title: 'MongoDB',
    author: 'Deepa',
    published_year: 2025
  },
  {
    _id: ObjectId('68851251fafe312e1eeec4ae'),
    title: 'NOSQL',
    author: 'vijay',
    published_year: 2023
  }
]

library> db.books.find()
[
  {
    _id: ObjectId('68850d74fafe312e1eeec4ab'),
    title: 'The Tata story',
    author: 'Peter Casey',
    published_year: 2018
  },
  {
    _id: ObjectId('68851100fafe312e1eeec4ac'),
    title: 'ignited minds',
    author: 'Dr.Apj Abdul Kalam',
    published_year: 2002
  },
  {
    _id: ObjectId('68851216fafe312e1eeec4ad'),
    title: 'MongoDB',
    author: 'Deepa',
    published_year: 2025
  },
  {
    _id: ObjectId('68851251fafe312e1eeec4ae'),
    title: 'NOSQL',
    author: 'vijay',
    published_year: 2023
  }
]
library>




QUERIES AND EXPLANATION:

//Create operation

1.use library - (switch to or create a database named library)
2.db.library.books - ( it’s a reference path to a collection inside a database)
3.db.books.insertOne({title:"ignited minds",author:"Dr.Apj Abdul Kalam",published_year:2002}) - (Inserts one document into the collection.if the collection doesn't exixst yet,mongodb will automatically create it)


//READ OPERATION

1.db.books.find() - (This is the query method that retrieves documents from the collection and all documents stored in the books collection)
2. db.books.find({author:"Peter Casey"}) - (It searches for all books written by "Peter Casey" and returns them and Only the document(s) with author: "Peter Casey" are returned)
3. db.books.find().sort({published_year:1}).limit(1) - (It finds the book with the earliest published year in the books collection)

//UPDATE OPERATION

1.db.books.updateOne({title:"The Tata story"},{$set:{published_year:2025}}) - (It finds the first document in the books collection where the title is "The Tata story" and updates the published_year field to the current year)
2.db.books.updateMany({},{$set:{genre:"Mystery"}}) - (It adds or updates the field genre to "Mystery" in every document inside the books collection)

//DELETE OPERATION

1.db.books.deleteOne({published_year:2025}) - (It deletes the first book document in the books collection with published_year equal to 2025)
2. db.books.deleteMany({published_year:{$lt:2003}}) - (It deletes all books from the books collection where published_year is before 2003)

//ADVANCED QUERY

1.db.books.find().sort({published_year:-1}).limit(3) - (It retrieves the 3 most recently published books from the books collection)
2.db.books.find({title:/MongoDB|NOSQL/i}) - (It searches for all books where the title contains either "MongoDB" or "NOSQL")





