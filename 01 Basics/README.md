# Basics

# Adding JS to webpage

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>

    <!-- Method 1 : writing script directly in script tag under HEAD/BODY -->
    <script>
        console.log("hi")
    </script>

    <!-- Method 2 : Invoking external js file in HEAD -->
    <script src="index.js"></script>

  </head>
  <body>

    <!-- Method 3 : Invoking external js file in end of BODY -->
    <script src="index.js"></script>

  </body>
</html>
```
# Comments

```javascript
// hi will be logged in console when page is loaded
console.log("hi");
```

# Browser console

<kbd>Ctrl + Shift + I</kbd> in browser opens a window which has console tab where one can directly write js. It also provided warning/errors in the code.