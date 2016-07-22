# node-red-flows

This a place for playground with [node red](http://nodered.org/)

I used postman to make all the web requests

##`watson-translator.json`
* requires a Watson Language translation service from Bluemix
  * use username and password given by the service
* use postman to generate the POST request to this url http://localhost:1880/translate
  * add the header `Content-Type = application/json`
  * add the follwing raw body
  ```json
  {
      "text":"one small step for men one giant leap for mankind",
      "target":"fr",
      "source":"en"
  }
  ```

##`watson-text-speech.json`
* requires a Watson Text toSpeech service from Bluemix
  * use username and password given by the service

In the browser type the url [http://localhost:1880/audio](http://localhost:1880/audio) keep this page open.
Then press the inject button on the flow. The web page (http://localhost:1880/audio) should speak out the text contained in the inject module. Open the inject module and change the text.


##`mashup-watson-translator+text-speech.json`
This combines watson-translator.json and watson-text-speech.json
* the POST request is made to http://localhost:1880/translate_speech
* the audio is heard at this url http://localhost:1880/translate_speech_audio
 
##`get-request-triggers-ifttt.json`
* make sure the event and the apikey in the ifttt url is replaced with the relevant information from your receipy
This shows how to get a ifttt reciepy containing the Maker module to send an email when the the request is sent.
The url to go to in the browser is `http://localhost:1880/test-ifttt`

## `insert-find-in-mogodb.json`
* insert data in a mongodb collection
  * POST request http://localhost:1880/mongodb-insert
  * body of the request (example only)
   ```json
   {
   	"first":"arnold",
   	"last":"schwarzenegger",
   	"dob":"03/06/1925",
   	"gender":"m",
   	"hair_colour":"brown",
   	"occupation":"actor",
   	"nationality":"american"
   }
   ```
or for multiple insert
   ```json
   [{
   	"first":"arnold",
   	"last":"schwarzenegger",
   	"dob":"03/06/1925",
   	"gender":"m",
   	"hair_colour":"brown",
   	"occupation":"actor",
   	"nationality":"american"
   },
   {
   	"first":"tony",
   	"last":"curtis",
   	"dob":"21/04/1978",
   	"gender":"m",
   	"hair_colour":"brown",
   	"occupation":"developer",
   	"nationality":"american"
   }]
   ```
   
* find data in a mongodb collection
  * POST request http://localhost:1880/mongodb-find
  * body of the request (example only)
   ```json
   {
    "gender":"f"
   }
   ```

## `ifttt-maker-email-channels.json`
For this flow you need a [ifttt](https://ifttt.com/) account so that you can produce a receipy with the Maker and email channels. The idea is that when the POST request to http://localhost:1880/ifttt with the body {"value1":"some value", "value2":"some value", "value3":"some value"} is received an email is sent to the email address set in the email channel. The values contained in the body will also be part of the email.
* In the module web request replace the event name and the apikey with your own 
https://maker.ifttt.com/trigger/{event}/with/key/apikey
* POST request http://localhost:1880/ifttt
  * body of the request (example only)
   ```json
   {
    "value1":"some value", 
    "value2":"some value", 
    "value3":"some value"
   }
   ```

## `image-classifier.json`
This flows can be used with any trained models.
This is the url to use
`http://localhost:1880/recognise_nike?url={url to the image}&classifier_id={nike classifier}&version={version}&apikey={api key}`
or go to this url 
`http://localhost:1880/recognise_nike` 
and enter the necessary information in the form
