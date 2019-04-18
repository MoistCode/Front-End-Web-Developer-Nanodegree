# Front-End-Web-Developer-Nanodegree

## The Building Blocks of Front-End
---
### HTML Syntax

- The `<head></head>` tag contains metadata such as title, script/css links
- https://validator.w3.org/#validate_by_input can help validate HTML
- HTML Document usually starts with a type declaration
  - Helps browser determine type of HTML document is trying to parse and display (rendering mode)
  - Example below triggers standard mode but specifies an older form of validation
```html
  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TY/html4/strict/dtd">
```
  - Example below triggers "Quirks" mode. This is bad.
```html
  <html>
    ...
  </html>
```
  - Newer websites normally have this declaration which triggers standard mode with all updated features.
```html
  <!DOCTYPE html>
```

- Quirks Mode and Standards Modes
  - Three modes:
    - Quirks
      - Emulate nonstandard behavior in Navigatory 4 and IE 5
      - Support websites built before standards
    - Almost Standard
      - Small number of behaviors from `Quirks`
    - Standard
      - Behaves according to HTML/CSS specifications
  - You can find out what mode is used by going into dev tools then document mode

---
### CSS Syntax

- Cascading Style Sheets
- Ruleset composes of a selector and a declaration block
- Attributes helps describe content
- CSS Units
  - Absolute
    - Fixed units of measurement
    - px, mm, in, cm
  - Relative
    - Comparison to another element
    - %, em, vw, vh
- Browsers select font-family from left to right
  
  
---
### Responsive Design

- Remote debugging
  - Android
    - Turn on dev mode on device
      - About > Build Number x 7 > USB Debugging (on)
    - Chrome Canary (laptop)
      - Chrome://inspect
    - Chrome Beta
  - iOS
    - https://github.com/google/ios-webkit-debug-proxy
- Not all devices have the same pixel density
  - Not all pixels are created equal
  - Browser reports width in browser independent pixel
    - Unit of measure of a pixel to a real distance
    - The same regardless of the pixel density of the display
    - 1280 DIPs => 2560 hardware pixels
  - No meta viewport?
    - No viewport set means the browser assume it's not suppose to work on a small screen
    - Renders as if the screen is 980 DIPs wide
      - Really small
    - Browser then uses font-boosting and makes it even uglier by increasing certain fonts and leaving others really small
  - Tech spec pixels are hardware pixels
  - Device pixel ratio
    - Horizontal
  - Font boosting
  - Calculate CSS pixels from hardware pixels
    - Hardware pixel / DPR
- Setting the viewport
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
  - This tells the browser we know what we are doing
  - Allows page to reflow content to match screen sizes
  - Establish a 1-to-1 relationship between DIP and CSS pixels
  - If this is not in the head, content stays the same when switching from landscape to portrait
- max-width: 100% prevents overflowing
  - Recommend this as a catch-all for `img`, `embed`, `object`, `video`
- Tap targets
  - Anything a user might interact with
  - Needs to be big enough for users to hit on mobile
  - Small enough not to hit two
  - Fingers are about 40 css pixels length
    - Make at least 48 x 48 px to be safe
    - min-width/height: 48px
    - Using width or height alone won't allow the element to resize if the content inside is bigger than the container
  - Mobile first design
    - Prioritize content
    - Performance
  - Flexbox practice
    - https://s3-us-west-2.amazonaws.com/gae-supplemental-media/pattern-mostly-fluid-quiz-blankcsshtml/pattern-mostly-fluid-quiz-blankcss.html
- Media queries 
  ```html
    <link rel="stylesheet" media="screen and (min-width: 500px)" href="over500.css">
  ```
  ```css
    @media screen and (min-width: 500px) {
      ...
    }
    @import url("no.css") only screen and (min-width: 500px);
  ```
  - DO NOT USE `@import`
  - Linked CSS vs @media
    - Linked CSS; lots of requests; smaller files 
    - @media; less request; bigger files
  - Most popular is max/min width
    - max/min-device-width is highly discouraged
  - Breakpoints 
    - Point at which the layout changes
    - Set breakpoints based off content
  - Complex media queries
  ```css
    @media screen and (min-width: 500px) and (max-width: 600px) {
      ...
    }
  ```
  - https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout
---
### Resposive Patterns
- Categories
  - Column drop
    - Narrow; stack
    - As viewport gets wider; content goes up one by one
    - Margins are added to left and right at max width
  - Mostly fluid 
    - Similar to column drop but more gridlike
    - Narrow; stacks
    - As viewport gets wider; grid starts showing
  - Layout shifting
    - Most responsive
    - Way that content moves 
    - Flexbox really shines due to ordering
    - Requires more planning
  - Off canvas
    - Places less used content on the side
    - Nav in mobile that comes in from the side when hamburger is clicked
---
### Optimizations
- Responsive tables
  - Hidden columns 
    - Hides columns based on importance
    - Biggest issue is hiding content
  - No more tables
    - Table is collapse
    - Turns into a list
    - All data is visible
    - Every column becomes a row
    - content: attr(data-th)
  - Contained tables
    - Wrap it in a div
      - overflow-x: auto
      - width: 100%
    - Horizontal scroll
- Fonts
  - Words per line matters
  - Can't be too long or too short
  - Ideal measure is anywhere from 45 to 90 cpl ( ~65 cpl)
  - Big enough to read
  - Line height is important
  - Base shoud be around at minimum 16px
---
### Documentation
- https://github.com/udacity/ud777-writing-readmes
- Both for yourself and others
- Anatomy
  - Title
  - Description
  - Installation
  - Usage
- What steps?
- What should users have installed/configured?
- What might they have a hard time understanding right away?
- Markdown is a good language
  - Translates to HTML
  - Makes it easy to skim through
  - https://help.github.com/en/articles/basic-writing-and-formatting-syntax
  - https://dillinger.io/
---
### JavaScript
- Hoisting
  - Before execution
  - Variables are raised to the top of the function scope
  - Runtime is when variables are assigned and when functions are ran
  - `let` and `const` are block-scoped, not function-scoped like `var`
- Always declare using `const` unless variable will change
- No real reason to use `var` anymore
- Template literals don't require newline since they perserve newlines
  - Can be multiline
- Array destructuring
  - const [a,b] = ['based off', 'index];
  - const [a, , b] = ['based off', 'ignored', 'index];
- Object destructuring
  - const {a,b} = {a: 'based off', b: 'keys'};
- Shorthand method names
  - const gemstone = { calc() {} }
- Iteration
  - i for iterator
  - for..of for objects
  - for..in can be in big trouble due to extra method in array prototype
    - Loops over all enumerable properties
    - Discouraged for arrays
- Rest and Spread
  ```js
    function syum(...nums) {
      let total = 0;
      for(const num of nums) {
        total += num;
      }
      return total;
    }
  ```
---
### DOM
- DOM Creation
  - HTML received
  - HTML tags converted to tokens
  - Tokens converted to nodes
    - DOCTYPE
    - start tag
    - end tag
    - comment
    - character
    - end of file
  - Nodes converted to DOM
  - HTML -> Token -> Node -> DOM(tree structures; relationships between nodes)
  - Node vs node
    - Node = blueprint
    - node = object
  - Node vs Element interface
- innerText vs textContent
  - textContent
    - set text content of an element and all its descendants
    - return text content of an element and all its decendants
    - will display html text as text unlike innerHTML
  - innerTEXT
    - As it would be seen with CSS
- Event phases
  - Capture
    - HTML down to element
  - At target
    - At element
  - Bubbling
    - Element back up to top of HTML
---
### Performance
- monitorEvents(document)
- performance.now()
- Why use `div` holder?
  - Browser has to run through reflow calc to determine the new screen layout
  - Then repaint the screen
  - Adding to document will cause a constant reflow and repaint process
  - `DocumentFragment`
- Reflow
  - Process of browser laying out the page
  - Happens when you first display the DOM
    - Generally after the DOM and CSS has been loaded 
    - Happens again every time something changes the layout
    - Very expensive process
- Repaint
  - Happens after reflow as the browser draws the new layout to the screen 
  - Quicker but still should be limited
- Adding a little CSS change can cause a reflow
- Use position fixed or absolute when making complex rendering changes such as animations
- Use less descendent selectors and complex CSS
- Less depth in HTML hierarchy; less is more
---
### Web Accessibility
- Shorten it to `a11y`
- Perceivable, operable, understadable, robusts (POUR)
- Focus refers to moving to each functionality such as clicking on an input field
- Logical tab order
- Implicitly focusable
  - Button, input
- It is possible to use CSS to visually change the order but the DOM element is still ordered in a certain way
  - Tab will still go by the tab order, not the visual order
  - Ensure meaningful sequence
- Tabindex
  - -1 indicates it's not in the natural tab order
  - Can be focusable with `focus()` JS 
  - 0 is in the natural tab order
  - Tabindex greater than 0 is an anti-pattern
  - Usually put on something a user may interact with
  - Some exceptions
    - Click that changes content
    - Click that zenscrolls down
    - Manage focus
- Skip links
  - Help users to move straight to the main content
  - use `:focus` selector to bring it into view
- Check ARIA Authoring Best Practice Docs
- Roving focus
  - Custom widget
  - i.e., make a custom radio group accessible
- Navigation pop up menu
  - Tab order can hide tab in a hidden menu
  - `document.activeElement` will you a reference to the current active element
  - Using `display: none` or `visibility: hidden` helps with this
- Chrome accessibility dev tools
- Keyboard traps
  - Useful for modal windows but not for anything else
- Semantics
  - Affordances
    - Patterns
  - Accessibility tree sort of looks like a web page from the 90s
    - Only information necessary to understand content
  - Visible label
    - Form buttons has descriptive values
  - Text alternative
    - Not visible
      - image alt
    - Input elements should have a name
      - We can wrap checkboxes in a label or use a label `for` attr
    - Use learn more about ... vs learn more
- ARIA
  - Web Accessibility Initiative Accessible rich internet application
    - WAI-ARIA
    - When native HTML won't be enough
      - Ex. Checkbox
        - Using a DIV won't indicate that it is a checkbox or its state
        - `role="checkbox" aria-checked="true/false"`
  - Only modify the accessibility tree
    - Does not:
      - Modify appearance or behavior
      - Add focusability or event handling

---
### JavaScript
- Symbols
  - New datatype
  - Unique identify 
  - Mainly used to identify properties within an object
    - Banana1 .... BananaN
  ```js
    const sym1 = Symbol("apple");
    const sym2 = Symbol("apple");
    console.log(sym1 === sym2); // false

    const bowl = {
      [Symbol('apple')]: { color: 'red', weight: '155ox' },
      [Symbol('apple')]: { color: 'green', weight: '145ox' },
    }
  ``` 
- Iterables
  ```js
    const digits = [1,2,3,4,5,6];
    for(const digit of digits) {
      console.log(digit);
    }
  ```
- Iteraor 
  ```js
    const digits = [1,2,3,4,5,6];
    const arrayIterator = digits[Symbol.iterator]();

    arrayIterator.next(); // Object { value: 1, done: false }
    arrayIterator.next(); // Object { value: 2, done: false }
    arrayIterator.next(); // Object { value: 3, done: false }
  ```