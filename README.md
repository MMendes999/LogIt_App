*I will be building a minimalistic Log application using the awesome NodeJs framework,
HapiJs, developed by Walmart Labs.*

*With this app you will be able to take note of your progress,
by creating logs of your daily performance in whichever area you wish.*

*This app will start-off small and simple, allowing you to create new logs,
delete logs, view and update existing logs.*

**So please take into consideration that this is a work-in-progress!**

---

##Why Hapi?

####For the following reasons:
* It is easy to implement (although there are not many working examples yet);
* It allows for a large amount of concurrent connections without forsaking performance levels(Walmart launched it on *Black Friday*) http://en.wikipedia.org/wiki/Black_Friday_(shopping)
* Has great documentation https://github.com/spumko/hapi
* Allows object schema validation with Joi https://github.com/spumko/joi
* Easy to test with Lab https://github.com/spumko/lab

It could have been easier to use [express](http://expressjs.com/), mainly because there are a lot more examples to follow, but what would be the fun in that right?

---

##Which Database?

Because Hapi is so recent, my major challenge was to select a database.

- [ ] Apache CouchDb - http://couchdb.apache.org/
- [ ] CouchBase - http://www.couchbase.com/wiki/display/couchbase/Home
- [ ] MongoDb - http://www.mongodb.org/

Performance wise, there is no major issue with any of these databases. This is not intended to be a big app with thousands of users.

---

###CouchDb

So bearing that in mind I started with *CouchDb*, but found I had trouble with connecting to the dabase while using tha HapiJs framework. Like I said there aren't that many examples to follow.
The documentation also seems to be presented in a not too friendly fashion. You might find it to be fine, but not for me.
I also found that I had trouble using or finding frameworks available to connect to CouchDb.

* See *ChouchDb* Vs *CouchBase* (http://www.couchbase.com/couchbase-vs-couchdb)

####I dumped *ChouchDb* and tried *CouchBase*.

---

###CouchBase

My first warning, is that when you install *CouchBase*, you should always install the 'Developer Preview':

```
npm install couchbase@2.0.0-dp1 --save
```

The documentation for *CouchBase* is easy to follow and there are many examples.
If you need an example reference using *couchBase* with *Hapi*, go to https://github.com/nelsonic/time

I ended up dumping *CouchBase* from my dependencies for no specific reason in particular other than learning MongoDb could be a major advantage at this time, for Mongo is currently one of the most popular databases in use.

---

###MongoDb

The documentation for *MongoDb* is very clear and well organised.
There are lots of examples to follow.

http://www.mongodb.org/

*I found it tricky to use mongoose directly with Hapi.*

*Once a connection opens, a callback will be called. For brevity, let's assume that all following code is within this callback.*

http://mongoosejs.com/docs/index.html
```
var db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', function callback () {
  // yay!
});
```
*I have not yet found a solution to this.*

I seem to have found an alternative with the *mongoose-simpledb* module.

See this video in particular to learn how to connect to *MongoDb* while using **Hapi.js**:
* https://www.youtube.com/watch?v=CIPbmPUKyMI

The module used in this video (*mongoose-simpledb*) can be found at: https://www.npmjs.org/package/mongoose-simpledb


---

**In summery, so far my main problem has been finding a way to connect to
the databases with a module that is easy to use, well maintained and
tested and with examples using tha Hapi.js framework!**
