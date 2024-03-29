# cypress - Mochawesome(Reporter)
cypress reporter with mochawesome

# Steps for Cypress
```
npm install cypress --save-dev
npx cypress open
```
[Documentation Cypress](https://docs.cypress.io/guides/getting-started/installing-cypress)

## Screenshots
![App Screenshot](https://user-images.githubusercontent.com/1271364/31740846-7bf607f0-b420-11e7-855f-41c996040d31.gif)

# Steps for mochawesome-reporter
```
npm i cypress-mochawesome-reporter
```
[Documentation Mochawesome Reporter](https://www.npmjs.com/package/cypress-mochawesome-reporter?activeTab=readme)

## Screenshots
![App Screenshot](https://raw.githubusercontent.com/LironEr/cypress-mochawesome-reporter/HEAD/docs/assets/failed-test-with-screenshot.png)

## Running Tests

To run tests, run the following command

```bash
describe('example to-do app', () => {
  beforeEach(() => {
    cy.visit('https://example.cypress.io/todo')
  })

  it('displays two todo items by default', () => {
    cy.get('.todo-list li').should('have.length', 2)
    cy.get('.todo-list li').first().should('have.text', 'Pay electric bill')
    cy.get('.todo-list li').last().should('have.text', 'Walk the dog')
  })

  it('can add new todo items', () => {
    const newItem = 'Feed the cat'
    cy.get('[data-test=new-todo]').type(`${newItem}{enter}`)
    cy.get('.todo-list li')
      .should('have.length', 3)
      .last()
      .should('have.text', newItem)
  })

  it('can check off an item as completed', () => {
    cy.contains('Pay electric bill')
      .parent()
      .find('input[type=checkbox]')
      .check()
    cy.contains('Pay electric bill')
      .parents('li')
      .should('have.class', 'completed')
  })

  context('with a checked task', () => {
    beforeEach(() => {
      cy.contains('Pay electric bill')
        .parent()
        .find('input[type=checkbox]')
        .check()
    })

    it('can filter for uncompleted tasks', () => {
      cy.contains('Active').click()
      cy.get('.todo-list li')
        .should('have.length', 1)
        .first()
        .should('have.text', 'Walk the dog')
      cy.contains('Pay electric bill').should('not.exist')
    })

    it('can filter for completed tasks', () => {
      cy.contains('Completed').click()
      cy.get('.todo-list li')
        .should('have.length', 1)
        .first()
        .should('have.text', 'Pay electric bill')

      cy.contains('Walk the dog').should('not.exist')
    })

    it('can delete all completed tasks', () => {
      cy.contains('Clear completed').click()
      cy.get('.todo-list li')
        .should('have.length', 1)
        .should('not.have.text', 'Pay electric bill')
      cy.contains('Clear completed').should('not.exist')
    })
  })
})
```

## Authors
- [@LironEr](https://github.com/LironEr/cypress-mochawesome-reporter)
- [readme.so(editor)](https://readme.so/editor)