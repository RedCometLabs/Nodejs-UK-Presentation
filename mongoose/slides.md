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

!SLIDE smaller
# Relationships
## DBRefs

    @@@ javascript
    var PersonSchema = new Schema({
        name    : String
      , age     : Number
      , stories : [{ type: Schema.ObjectId, ref: 'Story' }]
    });

    var StorySchema = new Schema({
        _creator : { type: Schema.ObjectId, ref: 'Person' }
      , title    : String
      , fans     : [{ type: Schema.ObjectId, ref: 'Person' }]
    });

    var Story  = mongoose.model('Story', StorySchema);
    var Person = mongoose.model('Person', PersonSchema); 

!SLIDE small
# Relationships
## DBRefs

    @@@ javascript 
    Story
    .findOne({ title: /Nintendo/i })
    .populate('_creator') // <--
    .run(function (err, story) {
      if (err) ..
      console.log('The creator is %s', story._creator.name);
      // prints "The creator is Aaron"
    })

!SLIDE bullets incremental
#Middleware
* Method Hooks
* Called before `save`, `init` and `remove`
* Can be run in series or parallel

!SLIDE 
#Middleware
## Series

    @@@ javascript
    schema.pre('save', function (next) {
      // do something cool
      next();
    })

!SLIDE small
#Middleware
## Parallel

    @@@ javascript
    schema.pre('save', true, function (next, done) {
      // do something also quite cool
      done();
    })



