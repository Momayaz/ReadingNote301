# Update/Delete
## Sending form data
.... what happens when a user submits a form — where does the data go, and how do we handle it when it gets there?

The ```<form>``` element defines how the data will be sent. All of its attributes are designed to let you configure the request to be sent when a user hits a submit button. The two most important attributes are action and method. The action attribute defines where the data gets sent.((no attributes, as below, the ```<form>``` data is sent to the same page that the form is present on:)). The method attribute defines how data is sent((get,post)).

## GET method
The GET method is the method used by the browser to ask the server to send back a given resource.

## POST method
It's the method the browser uses to talk to the server when asking for a response that takes into account the data provided in the body of the HTTP request.When the form is submitted using the POST method, you get no data appended to the URL

## TIPS
* If you need to send a password (or any other sensitive piece of data), never use the GET method or you risk displaying it in the URL bar, which would be very insecure.
* If you need to send a large amount of data, the POST method is preferred because some browsers limit the sizes of URLs. In addition, many servers limit the length of URLs they accept.
PHP
```
<form action="https://www.foo.com" method="POST">
  <div>
    <label for="say">What greeting do you want to say?</label>
    <input name="say" id="say" value="Hi">
  </div>
  <div>
    <label for="to">Who do you want to say it to?</label>
    <input name="to" id="to" value="Mom">
  </div>
  <div>
    <button>Send my greetings</button>
  </div>
</form>
```
```
<?php
  // The global $_POST variable allows you to access the data sent with the POST method by name
  // To access the data sent with the GET method, you can use $_GET
  $say = htmlspecialchars($_POST['say']);
  $to  = htmlspecialchars($_POST['to']);

  echo  $say, ' ', $to;
?>
```