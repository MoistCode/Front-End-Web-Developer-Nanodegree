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
