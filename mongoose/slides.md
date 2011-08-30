!SLIDE bullets incremental
# What is it
* Mature Mongodb ORM
* Developed by the LearnBoost team
* Designed specifically for nodejs

!SLIDE commandline incremental
# Installation
    $npm install mongoose
    Installing...Done

!SLIDE
# The basics

!SLIDE small
# Define Model

    @@@ javascript
      var Comment = new Schema({
          name  :  { type: String, default: 'hahaha' }
        , age   :  { type: Number, min: 18, index: true }
        , bio   :  { type: String, match: /[a-z]/ }
        , date  :  { type: Date, default: Date.now }
      });

!SLIDE
# Crud

!SLIDE small
# Simple Queries

    @@@ javascript
    User.find({ 'some.value': 5 }, function (err, docs) {
    // docs is an array
    });

    User.findById(obj._id, function (err, doc){
    // doc is a Document
    });

!SLIDE
# Complex Queries

    @@@ javascript

    User
      .select('name', 'age', 'tags')
      .where('age').gte(25)
      .where('tags').in(['movie', 'music', 'art'])
      .skip(20)
      .limit(10)
      .asc('age')
      .run(callback);

!SLIDE 
# Relationships
## Embedded Docs

    @@@ javascript
    var Post = new Schema({
        title     : String
      , comments  : [Comment]
    });


