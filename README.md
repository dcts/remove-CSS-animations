# REMOVE CSS ANIMATIONS (for faster scraping)

This repo is a shortcut to remove css transitions, transformations and animations from a webpage for a faster scraping experience. To recap:
- **transistions**: transform css properties (width, color etc.)
- **transformations**: when usm transform functions like `scale`, `skew`, `rotate` etc..
- **animations**:

```js
let filePath = "https://dl.dropboxusercontent.com/s/ep1nzckmvgjq7jr/remove_transitions_from_page.css";
let html = `<link rel="stylesheet" type="text/css" href="${filePath}">`;
document.querySelector("html > head").insertAdjacentHTML("beforeend", html);
```
