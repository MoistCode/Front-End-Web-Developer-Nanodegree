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