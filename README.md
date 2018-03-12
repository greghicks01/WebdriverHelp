# WebdriverHelp

This project covers five strategies I have successfully used to make stable webdriver UI tests.

Patterns in the UI plus a good locator convention can reduce the test code base by 30% or more.

Saleforce chose a consistent way to mark up a set of display screens that resulted in almost 80% reduction of the code base, even with iframes.

Pattern Overview
* Direct
* Group
* Container
* indexed
* Workflow

Using the patterns requires a little research in the target html, looking for names, classes or other locator that the driver patterns can use.

|Strategy	| Used | Description 
| --- | --- | ---
|Direct	| A few objects can be accessed by a locator per object	| Login screens usually have 3-5 UI objects available and are suitable for a direct strategy approach.
|Group |	A number of objects, like buttons or links, selected based on their label	Group extracts all objects matching a particular type. There may be more than one type (eg a standard button and an input with a class of 'btn'). The group has all non-displayed members removed and iterates over the remainder to find  the right object before acting on it. *Function clickButton("label");*
|Container |	Interactive UI objects like a calendar use the container as the primary identifier and dynamic techniques to interact with the rest of the container |	Once the container is identified, direct, group or indexing are used to access the remaining parts of the container. Eg calendar with two drop lists and a table for the selected month. Always access the inner objects relative to it and only use the minimum object count to achieve automation.
|Indexer|	Many objects with identifying labels |	Reduces code across busy web pages. Access to the developers enhances the strategy with the use of class attributes as the identifier. Indexers take two values, Label and Value to find the right object to write to and to confirm the data saved. Get and set code operates on a dictionary or hash of *<string,IWebElement> *
|Workflow|	Sometimes screens have popout dialogs to improve data entry. |	Workflow combines step implementation with the interface to handle complex UI interactions
