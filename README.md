# node-red-flows

This a place where I copy flows from other places and mach them up for my own use

##`watson-translator.json`
* requires a Watson Language translation service from Bluemix
  * use username and password given by the service
* use postman to generate the POST request
  * add the header Content-Type = application/json
  * add a raw body
```json
{
    "text":"one small step for men one giant leap for mankind",
    "target":"fr",
    "source":"en"
}
```
In the browser type the url [http://localhost:1880/translate](http://localhost:1880/translate)
