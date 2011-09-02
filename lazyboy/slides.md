!SLIDE center
# LazyBoy
![couchdb](couchdb.jpg)


!SLIDE bullets incremental
#LazyBoy
## Aim:
* Intuitive api
* Remove boiler plate db code
* Support defaults and basic relationships

!SLIDE commandline incremental
# Installation 
    $npm install lazyboy
    Installing...Done

!SLIDE 
# Define Model
    @@@ javascript 
        var Model = require('LazyBoy');
      
      var User = Model.define('User', {
        name: String
        surname: {type: String, default: "Rambo"}
      });

!SLIDE smaller
# Crud
  
    @@@ javascript

    var rambo = User.create({name: "John", surname: "Rambo"});

    rambo.save(function (err, saved_user) {
      if (err) throw err;

      console.log("Awesome, I got saved with id " + saved_user.id);
    });

    rambo.remove();

!SLIDE bullets incremental
# Queries
* Couchdb uses views
* Lazyboy creates some standard views

!SLIDE small
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

!SLIDE bullets incremental
# Other features
 * Custom views and methods
 * Save and create hooks
 * Model embedding



