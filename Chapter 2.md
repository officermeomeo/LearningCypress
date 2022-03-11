Some of the checks Cypress does by default are:
1. it ensures that no element is hidden.
2. it ensures that the element is not disabled.
3. it ascertains that the element is not detached.
4. it ensures that the element is not read-only.
5. In addition to the above, it ensures that the element is not animating.
6. it makes sure that the element is not covered.
Moreover, it scrolls the element in port-view.
Finally, it scrolls the element to fix the position if covered by another element.

Also Cypress manages a Promise chain on our behalf, with each command yielding a 'subject' to the next command, until the chain ends or an error is encountered.

Cypress runs commands asynchronously, these  commands don't do anything at the moment they are invoked, but rather enqueue themselves to be run later.
Eg: 

it('Changes the URL when "awesome" is clicked' , () => {
cy.visit('/my/resource/path') // Nothing happens yet
cy.get('.awesome-selector') // Still nothing happening
    .click() // Nope, nothing

  cy.url() // Nothing to see, yet
    .should('include', '/my/resource/path#awesomeness') // Nada,not hapenning.
});
};

// Ok, the test function has finished executing...
// We've queued all of these commands and now... ...




Mixing Async and Sync code:

