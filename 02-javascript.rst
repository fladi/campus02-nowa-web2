:data-transition-duration: 2000
:skip-help: true
:css: css/campus02.css

.. role:: javascript(code)
  :language: javascript

.. role:: html(code)
  :language: html

.. title: JavaScript

----

JavaScript
----------

* XMLHttpRequest
* jQuery.ajax

----

XMLHttpRequest
--------------

Ohne externe Abhängigkeiten, nur JavaScript.

.. code:: javascript

  var req = new XMLHttpRequest();
  req.open('GET', 'https://example.org/');
  req.send();

Kompatibel ab *Edge 12*, *Firefox 12*, *Chrome 31*, *Safari 7.1*, *Opera 18* und
*Android 4.4.4*.

----

Events
------

======================= ====================================================================
Event                   Beschreibung
======================= ====================================================================
:javascript:`loadstart` Der HTTP-Request wird gesendet
:javascript:`progress`  Daten werden an den Webserver übertragen.
:javascript:`abort`     HTTP-Request wurde abgebrochen.
:javascript:`error`     Ein Fehler ist aufgetreten.
:javascript:`load`      Der HTTP-Request war erfolgreich.
:javascript:`timeout`   Der HTTP-Request wurde nicht in der festgelegten Zeit abgeschlossen.
:javascript:`loadend`   Der HTTP-Request ist abgeschlossen (Erfolg oder Fehler).
======================= ====================================================================

----

JSON empfangen
--------------

Verwendet HTTP-Methode ``GET`` und :javascript:`JSON.parse` für HTTP-Response.

.. code:: javascript

  var req = new XMLHttpRequest();
  req.setRequestHeader('Accept', 'application/json');
  req.addEventListener('load', function() {
    console.log(JSON.parse(this.response));
  });
  req.open('GET', 'https://example.org/');
  req.send();

----

JSON senden
-----------

Verwendet HTTP-Methode ``POST`` und :javascript:`JSON.stringify` für
HTTP-Request-Body in der :javascript:`send` Methode.

.. code:: javascript

  var data = {'foo': 'bar'};
  var req = new XMLHttpRequest();
  req.setRequestHeader('Content-Type', 'application/json');
  req.setRequestHeader('Accept', 'application/json');
  req.addEventListener('load', function() {
    console.log(JSON.parse(this.response));
  });
  req.open('POST', 'https://example.org/');
  req.send(JSON.stringify(data));

----

jQuery
------

Freie JavaScript-Bibliothek für:

* DOM-Navigation über CSS3 Selektoren
* DOM-Manipulation
* Event-Handling
* Animationen und Effekte
* AJAX

----

jQuery: Verwendung
------------------

In HTML einbinden:

.. code:: html

  <script src="/path/to/jquery.js"></script>

In JavaScript-Code verwenden:

.. code:: javascript

  $('h1').addClass('blue').slideUp('slow');

----

jQuery: Events
--------------

.. code:: javascript

  $(document).ready(function() {
    $("div.test a").on('click', function() {
      alert("Hello world!");
    });
  });

----

jQuery AJAX (GET)
-----------------

.. code:: javascript

  var a = $.ajax({
    url: "https://example.org/",
    method: "GET",
    dataType: 'json'
  });
  a.done(function(msg){
    console.log(msg);
  });
  a.fail(function(){
    console.log('Error: ' + this);
  });

----

jQuery AJAX (POST)
------------------

.. code:: javascript

  var d = {'foo': 'bar'};
  var a = $.ajax({
    url: "https://example.org/",
    method: "POST",
    data: JSON.stringify(d),
    contentType: 'application/json',
    dataType: 'json'
  });
  a.done(function(msg){ console.log(msg); });
  a.fail(function(){ console.log('Error: ' + this); });
