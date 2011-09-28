!SLIDE center
# LazyBoy
### http://garrensmith.com/LazyBoy
![couchdb](couchdb.jpg)

!SLIDE bullets incremental
#LazyBoy
## Aim:
* Intuitive api
* Remove boiler plate db code
* Support defaults and basic relationships

!SLIDE commandline incremental
# Installation 
    $npm install LazyBoy
    Installing...Done

!SLIDE smaller
# Define Model
    @@@ javascript 
        var Model = require('LazyBoy');
      
      var User = Model.define('User', {
        name: String
        surname: {type: String, default: "Rambo"}
      });

!SLIDE center
# Crud
![cook](cook.jpg)
#### http://www.flickr.com/photos/st3f4n/3573062519/sizes/z/in/set-72157616350171741/ by Stéfan


!SLIDE smaller
# Crud
  
    @@@ javascript

    var rambo = User.create({name: "John", surname: "Rambo"});

    rambo.save(function (err, saved_user) {
      if (err) throw err;

      console.log("Awesome, saved with" + saved_user.id);
    });

    rambo.remove();

!SLIDE bullets incremental
# Queries
* Couchdb uses views
* Lazyboy creates some standard views

!SLIDE smaller
# Queries

    @@@ javascript

    User.find(user_id, function (err, user) {
      if (user) {
        console.log("I once was lost but now I'm found");
      }
    });

    User.where("surname","Rambo", function (err, users) {
      // all the users with "Rambo" surname
    });

!SLIDE smaller
# Relationships

    @@@javascript
    Comment = Model.define("Comment", {
      name: String,
      text: String
    });
    
    BlogPost = Model.define("BlogPost", {
      title: String,
      comments: {has_many: Comment}
    });

!SLIDE bullets incremental
# Other features
 * Custom views and methods
 * Save and create hooks



