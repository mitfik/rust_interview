## Rust interview

A test project for a Rust Developer position.

One of the TDA core concepts from the technology perspective is a MicroLedger concept utilization. Lets create a foundation for it and allow to exchange information (ie. an `Event` resource) via a dedicated transport layer. Imagine that this information may be exchanged among multiple instances of MicroLedger, but for the sake of simplicity, lets assume that only two instances at a time will be available and operating.

Requirements:

* Implement a Program which is able to run from command line and will support such options:
```
./program_name -H host:port -m human_readable_message_to_send_to_the_other_instance -t auth_token
```
where:
```
-H -- is the host:port of the other instance to connect to, ie: localhost:12345;
-m -- message to be sent to the other instance, ie: "Alice has a cat";
```
* Pair with the other instance knowing `host:port` -- for the sake of simplicity, you can use HTTP protocol here; In order to pair, use `GET /pair` endpoint, which will return the authentication token for any further request to be made;
* Prepare the `Event` structure:
```
struct Event {
  uuid: String,
  msg: Message
}
struct Message {
  payload: String
}
```
which will be sent to the other instance.
* Use `POST /messages` endpoint to send the message to the other instance and use JSON format to serialize the data;
* Spawn a new Cargo pkg and setup Github repository, where you'll upload the result of your work;
* Provide README.md with essential info how to run it with some examples.

### Caveats

Since it's more a concept app, it’s perfectly fine to make some compromises:

* you can use whatever technology/framework is suitable for you (yet, please don't use a sledgehammer to crack a nut), the only interesing part is the enduser is able to run it and see the result;


Don't be neither too generic nor too specific – don't polish it too much, but also keep focus on the code as well  – your final product should be „just enough”.
* if you don't feel prepared for the job, either get familiar with languages/technologies you'd consider useful here, or let us know you're not ready for it;
* we'll notice if you've worked on it a week instead of a few hours – don't do more than it's specified in the requirements;


Your work should be available via GitHub as a public repository, commit often[1].

Value quality over quantity. And, finally, when in doubt – especially about the scope of the task – feel free to ask.


\[1\]: Get familiar with SRP principle (if you don't know it yet) and apply it to commits. Get familiar with this https://chris.beams.io/posts/git-commit/ . 
