(from <https://lisperator.net/ymacs/>)

## build

```
npm install
npx parcel build --no-source-maps
```

find assets in the `dist` folder

## usage

```
<link rel="stylesheet" type="text/css" href="ymacs.css"/>
<link rel="stylesheet" type="text/css" href="themes/standard-light.css"/>

<script type="module">
 import { Ymacs, Ymacs_Buffer } from "ymacs.mjs";
 let buf = new Ymacs_Buffer({ name: "test.html", code: "<h1>Hello World</h1>" });
 let ymacs = new Ymacs({ buffers: [ buf ] });
 ymacs.addClass("Ymacs-line-numbers");
 ymacs.setColorTheme("standard-light");
 buf.cmd("html_mode");
 document.querySelector("#container").appendChild(ymacs.getElement());
 ymacs.focus();

 // prevent accidental tab killing (C-w) if focus is within Ymacs
 window.addEventListener("beforeunload", preventKill);
 function preventKill(ev) {
     if (document.activeElement.closest(".Ymacs")) {
         ev.preventDefault();
         return ev.returnValue = true;
     }
 }
</script>
```

Note that you should load at least one theme.
