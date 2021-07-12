---
id: 589690e6f9fc0f352b528e6e
title: Riordinare il progetto con i moduli
challengeType: 2
forumTopicId: 301549
dashedName: clean-up-your-project-with-modules
---

# --description--

Al momento, tutto il codice è compreso nel file `server.js`. Questo può portare ad un codice difficile da mantenere a poco espandibile. Crea 2 nuovi file: `routes.js` e `auth.js`

Entrambi dovrebbero iniziare con il codice seguente:

```js
module.exports = function (app, myDataBase) {

}
```

Ora, all'inizio del tuo file del server, richiedi questi nuovi file così: `const routes = require('./routes.js');` Subito dopo aver stabilito con successo una connessione al database, crea un'istanza per ciascun file, in questo modo: `routes(app, myDataBase)`

Infine, trasferisci tutte le rotte presenti nel tuo server e incollale nei nuovi file. Inoltre, prendi la funzione `ensureAuthenticated` dato che è stata creata specificamente per il routing. Ora, dovrai importare correttamente in cima al tuo file `routes.js` le dipendenze che vengono utilizzate, come `const passport = require('passport');` al di sopra della linea di export.

Continua ad aggiungere percorsi fino a quando non ci saranno più errori e il tuo file server non avrà più neanche una rotta (**ad eccezione della rotta nel blocco catch**)!

Now do the same thing in your auth.js file with all of the things related to authentication such as the serialization and the setting up of the local strategy and erase them from your server file. Be sure to add the dependencies in and call `auth(app, myDataBase)` in the server in the same spot.

Submit your page when you think you've got it right. If you're running into errors, you can check out an example of the completed project [here](https://gist.github.com/camperbot/2d06ac5c7d850d8cf073d2c2c794cc92).

# --hints--

Modules should be present.

```js
(getUserInput) =>
  $.get(getUserInput('url') + '/_api/server.js').then(
    (data) => {
      assert.match(
        data,
        /require\s*\(('|")\.\/routes(\.js)?\1\)/gi,
        'You should have required your new files'
      );
      assert.match(
        data,
        /client\s*\.db[^]*routes/gi,
        'Your new modules should be called after your connection to the database'
      );
    },
    (xhr) => {
      throw new Error(xhr.statusText);
    }
  );
```

# --solutions--

```js
/**
  Backend challenges don't need solutions, 
  because they would need to be tested against a full working project. 
  Please check our contributing guidelines to learn more.
*/
```