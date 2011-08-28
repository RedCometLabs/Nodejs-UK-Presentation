!SLIDE bullets incremental
# About
* Mongodb ORM
* By LearnBoost team

!SLIDE commandline
# Installation
    $npm install mongoose
    Installing...Done

!SLIDE
# Define Model

@@@ javascript
var Comment = new Schema({
    name  :  { type: String, default: 'hahaha' }
  , age   :  { type: Number, min: 18, index: true }
  , bio   :  { type: String, match: /[a-z]/ }
  , date  :  { type: Date, default: Date.now }
  , buff  :  Buffer
});

