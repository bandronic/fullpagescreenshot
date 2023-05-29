# Full Page Screenshot
Capture full page screenshot as Bas64 from an HTML node

If you ever wanted to capture a full page screenshot of HTML rendered elements, but the usual browser extensions that capture full page still capture the visible area, you have a rendered dashboard or rendered canvas (not the element) that you want to capture and those extensions still capture just the visible area, you can use this.

In the debugger windows of the browser, in the console, paste and load the following script:

``` js
// Load this first
var script = document.createElement('script');
script.type = 'text/javascript';
script.src = 'https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js';
document.head.appendChild(script);
```

This will load html2canvas lib.

After loading the lib, paste the following script, making sure to change the root element for which you want to screenshot. This will output to console a base64 image you can then decode or open in a new tab. The reason why I did not open a new tab with it directly from the script is that some websites have policies blocking this.

``` js
// Change ROOT_ELEMENT_GOES_HERE to whatever root element ID you wish to screenshot
var area = document.getElementById("{ROOT_ELEMENT_GOES_HERE}");
html2canvas(area).then((canvas) => {
    const base64image = canvas.toDataURL("image/png");
    console.log(base64image);
});
```

You will receive the base64 code in the console to copy. You can use then a base64 to image decoder to decode the copied code.
