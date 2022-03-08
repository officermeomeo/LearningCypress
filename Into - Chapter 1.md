Cypress bundles jQuery and uses many of its DOM traversal methods.
  What are the similarities between Cypress and jQuery while querying DOM elements?
  Ans: Cypress uses jQuery's powerful selector engine to search and identify DOM elements.
All the Cypress methods to traverse DOM are just wrappers around JQuery methods.
Similar to the Cypress's get method, the jQuery $() method also returns a jQuery object "JQuery<HTMLObjectElement>", which can be used to invoke further jQuery functions.
  
  Disimilarity between Cypress and jQuery:
  1. jQuery is synchronous while Cypress is asynchronous 
  
  The get() method returns a promise, and the promise will resolve only when one finds the element.
  If the promise will reject, it will never execute the code under the then() method and makes the code much more readable.
  Where as in JQuery the execution is synchronous in nature.
  
  2. When queried element is not traceable.
  For a jQuery query, if it is not able to find the DOM element, it returns an empty jQuery collection. 
  So, we need to handle such scenarios explicitly.
  But, in the case of Cypress, no explicit handling of the search result need to be done. 
  Cypress automatically retires the query until either it has not found the element or it times out while querying the element which is 4/6 secs by default and can be customised.

  Example:
  cy.get('element_selector')
  .then((element) => { // this code will never execute if the element is not found
    doSomething(element)
  })
  
  the code inside .then() will never execute if the command chained before has an unresolved promise. Here, it means that .get() is able to find an element or not.
  
  Locators in Cypress:
  CSS selectors are used in Cypress as well.
  1. using ID (#)
  2. using class (.)
  3. using attribute (say name for some input) Eg: input[name="testuser"]
  
  
  Cypress manages a Promise chain on your behalf, with each command returning a ‘subject’ to the next command until the chain ends or an error encounters. 
  So, all the commands returning a chainable interface allows invoking any other Cypress command without explicitly using the "cy" object.
  
  
  Parent_Child chaining in Cypress:
  cy.get('#searchBox').within(() => {
  cy.get('input').type('Cucumber') // Only searches inputs within searchBox
})
  
  
  this can also be achieved using : cy.get(...).find(...)
  
  For Cypress assures the synchronous behaviour by writting wrappers over JQuery code, it also can support async task by using .then() and passing a CB function.
  Lets look for that and much more in our next chapter.
  
  
  
  
