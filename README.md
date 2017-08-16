# angular-cheat-sheet


# Observables && Promises

## promise
A Promise handles a single event when an async operation completes or fails. It is used in preference to callback functions in writing synchronus code. It returns a single value and is not cancellable. 

### syntax / methods
* new Promise(resolve, reject) => {}
* toPromise();
* then();
* pending
* fulfilled
* resolve
* rejected


## observable
An Observable is like a Stream and allows you to pass zero or more events where the callback is called for each event. It is cancellable. Uses Reactive Extensions (RxJS). Preferred over promises for Http requests. 



### syntax
* Observable provides operators like map, forEach, reduce, similar to an array
* subscribe
* unsubscribe



