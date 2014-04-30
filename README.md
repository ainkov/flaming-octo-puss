Visual debugging for PhantomJS / CasperJS
=================

It grabs the screen as PhantomJS or CasperJS sees it with `captureBase64('png')` and then it's POSTing this to the 
receiving end which displays the screenshot in your browser.


To get this working:

0. Grab the repo (and node.js if you don't have it)
1. run `npm install`
2. run `node server.js`
3. go to http://localhost:8001
4. use the code below in your phantom or casper script to update the image:

````
this.evaluate( function(img){
  __utils__.sendAJAX("http://localhost:8001/", 'POST', {'img' : img }, false);    
  }, 
  {'img' : this.captureBase64('png')} 
);
````