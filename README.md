# React component unit testing

## Background & resources

React is a JavaScript library for building user interfaces. It allows creation of Single Page Apps (SPAs) which can change data without reloading the page.

In this lesson we are going to be learning about the [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/). This library allows us to test each React component in isolation (unit testing).

The learning today is based on the excellent [React Testing Libary Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9gm4_-5UsNmLqMosM-dzuvQ) from [the Net Ninja](https://www.youtube.com/c/TheNetNinja). I recommend you watch all of these videos offline. You should also refer to the [React Testing Library Cheatsheet](https://testing-library.com/docs/react-testing-library/cheatsheet) for a quick reference to all the available functions in the library.

## Pre-requisites
* Installation of VSCode
* Installation of the [Chrome React Dev Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
* A basic understanding of React. We recommend the following tutorials:
   * https://reactjs.org/tutorial/tutorial.html
   * [Full Modern React Video Tutorial](https://www.youtube.com/playlist?list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d) 

## Getting started
1. Fork https://github.com/harblaith7/React-Testing-Library-Net-Ninja (click on Fork button at top of page and select to fork to your git account)
1. `git clone https://github.com/<your git account name>/React-Testing-Library-Net-Ninja`
1. `cd React-Testing-Library-Net-Ninja`
1. `git checkout 01-Starter-Project`
1. Open VSCode and select the React-Testing-Library-Net-Ninja folder, then bring up a terminal in the `React-Testing-Library-Net-Ninja` directory.
1. `npm install`

To run the sample React app type `npm start`

To run the tests, create another terminal window and type `npm run test` (or `npm run test -t <name of test class>`).

I will walk you through creating tests in the same way that the [React Testing Library video](https://testing-library.com/docs/react-testing-library/intro/) does.

## Your first test (Header.test.js)
```javascript
import { render, screen } from '@testing-library/react';
import Header from '../Header';


describe("Test suite for my Header component tests", () => { 

    test('check that the header appears correctly', () => {
        // 1. Render the component under test
        render(<Header title="My fantastic TODO application" />);

        // 2. Locate the element we want to interact with
        const headerText = screen.getByText("My fantastic TODO application");

        // 3. We assert it is in the DOM
        expect(headerText).toBeInTheDocument();
    });

})
```

## Example mock when using Routers (TodoFooter.test.js)
```javascript
import { BrowserRouter } from "react-router-dom"
import { render, screen } from '@testing-library/react';
import TodoFooter from '../TodoFooter';

const MockTodoFooter = ({ numberOfIncompleteTasks }) => {
    return (
        <BrowserRouter>
            <TodoFooter numberOfIncompleteTasks={numberOfIncompleteTasks}>
            </TodoFooter>
        </BrowserRouter>
    )
}

describe ("Todo Footer", () => {
    test('should render the correct number of incomplete tasks', () => {
        render(<MockTodoFooter numberOfIncompleteTasks={2} />);
    ....
```

## Simulating events (AddInput.test.js)
```javascript
        const inputElement = screen.getByPlaceholderText("Add a new task here...");
        fireEvent.change(inputElement, {target: {value:"Another task I need to do"}}) // changing the input text

        const button = screen.getByRole("button");
        fireEvent.click(button); // simulate button click
```

## Creating your own React app
We recommend following the [Simple React Shopping Cart for Absolute Beginners video course](https://www.youtube.com/watch?v=AmIdY1Eb8tY) and modifying this to suit your chosen application.
