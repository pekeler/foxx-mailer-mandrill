# The Mandrill Mailer App

The Mandrill mailer app provides a Foxx script and `Foxx.queues` job type for sending transactional emails with [Mandrill](https://mandrill.com/).

*Examples*

First add this app to your dependencies:

```js
{
  ...
  "dependencies": {
    "mailer": "mailer-mandrill:^1.0.0"
  }
  ...
}
```

Once you've configured both apps correctly, you can use it like this:

```js
var Foxx = require('org/arangodb/foxx');
var queue = Foxx.queues.get('default');

queue.push(applicationContext.dependencies.mailer, {
    from_email: 'postmaster@initech.example',
    to: [{email: 'john.doe@employees.initech.example'}],
    subject: 'Termination',
    html: '<blink>YOU ARE FIRED!</blink>'
});
```

## Configuration

This app has the following configuration options:

* *apiKey*: Your Mandrill API key. You can find or generate this on the Settings page.
* *maxFailures* (optional): The maximum number of times each job will be retried if it fails. Default: *0* (don't retry).

## Job Data

For full documentation of all job data options supported by Mandrill see [the official Mandrill API documentation](https://mandrillapp.com/api/docs/messages.JSON.html).

## License

This code is distributed under the [Apache License](http://www.apache.org/licenses/LICENSE-2.0) by Christian Pekeler.
