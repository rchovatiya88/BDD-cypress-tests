## Cucumber Notes

### In Cucumber there is a feature file and step defination files which get processed to set standards to write test cases in BDD format and write automated tests using BDD Syntax into code. 



## Example of a Feature file
    Feature: Borrowers age limitation so it turns out we can't be giving home loans to kids. So much for too big to fail


	Scenario: Borrower must be 18 
		Given: a standard 30 year fixed mortage 
		And: the borrowers DOB is "Feb 21 2001"
		And: the loan date is "Feb 21 2018"
		When: the loan is submitted to underwriting
		Then: we should see an error: 
		"""
		Borrower must be over 18
		"""

## Example of a Step Definatation i.e code

```javascript 
const {Given, When, Then } = require ('cucumber')
const { expect } = require ('chai')
const { fixture } = './myTestHelpers'
const { underWriting } = '../../app/underwriting'

Given ('a standard 30 year fixed mortgage', function() {
    this.loan = fixture('30_year_fixed.json')
})

When ('the loan is submitted to underwriting', function () {
    this.response = underWriting.submit(this.loan)
})

Then('Then we should see an error:', function (message) {
    expect (this.response.error).to.eql(message)
})
```

## Problem
    Why do we need BDD, To help bridge the gap of requirements and execution and better Communication between Business and Dev.

![Diagram](/images/comm.png)


## Solution

    How to interacte with complex systems 
    STATE => Context
    ACTION => Action
    NEW STATE => Outcome

![cucuexample](/images/cucuexample.png)
# BDD-cypress-tests
