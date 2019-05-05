Idiomatic JavaScript
====================

A collection of tips and tricks I saw online that helps to write idiomatic JavaScript. Please, feel free to submit your pull requests to add more.

Table of Contents
-----------------

* [Objects](#objects)
* [Helpers](#helpers)

Objects
-------

* Create a new object from a combination of other objects:

  ```javascript
  const newState = { ...state, ...changes };
  ```

  Source: https://twitter.com/jaffathecake/status/953579387726811136?s=12

* Conditional object extension:

  ```javascript
  const obj = {
    ...condition && { property: value },
  };
  ```

  Source: https://dev.to/jfet97/the-shortest-way-to-conditional-insert-properties-into-an-object-literal-4ag7

Helpers
-------

* Delay 'polyfill':

  ```javascript
  const wait = (timeout) => (new Promise(resolve => setTimeout(resolve, timeout)));
  ```

  Usage:

  ```javascript
  // Promises
  wait(500).then(() => doSomething());

  // async/await
  await wait(500);
  doSomething();
  ```

  Source: https://twitter.com/JakeDohm/status/1118973133443207179

* Go-like results handling[^1]:

  ```javascript
  function O_o(promise) {
    return promise.then(data => {
      if (data instanceof Error) return [data];
      return [null, data];
    }).catch(err => [err]);
  }

  // Usage:
  async function usageExample(params) {
    const [err, data] = await O_o(myPromise(params));

    if (err) {
      // Handle or throw.
    }

    // Do stuff with data.
    return data;
  }
  ```

  Source: https://twitter.com/davidwells/status/1119729914876284928

[^1]: Not quite idiomatic, but still cool and useful :-)
