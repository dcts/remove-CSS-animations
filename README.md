
# Remove CSS Animations (for faster scraping)

This repo is a shortcut to remove css transitions, transformations and animations from a webpage for a faster scraping experience. To recap:
- **transistions**: transform css properties (width, color etc.)
- **transformations**: functions like `scale`, `skew`, `rotate` etc..
- **animations**: keyframe animations etc.

# Usage
### Chrome Console
First test if this script works locally in your browser (chrome, firefox, etc). Open the page you want to disable animations and css transitions and then execute the following code inside the console:
```js
let filePath = "https://raw.githubusercontent.com/dcts/remove-CSS-animations/master/css/remove.css";
let html = `<link rel="stylesheet" type="text/css" href="${filePath}">`;
document.querySelector("html > head").insertAdjacentHTML("beforeend", html);
```

### Ruby Selenium
Once the script successfully runs in your browser, you can try to automate it from within your webscraper. This snipped assumes you have `selenium-webdriver` successfully installed and running and shows you how to remove fancy animations to improve the scraping speed.

**Example Page**: [CSS clock that uses transitions and animations](https://dcts.github.io/javascript30-codingChallenges/days/02/)

```ruby
# 1. require selenium webdriver gem
require 'selenium-webdriver'

# 2. initialize webdriver
@driver = Selenium::WebDriver.for :chrome

# 3. go to website with some css animations
@driver.get("https://dcts.github.io/javascript30-codingChallenges/days/02/")

# 4. disable animations (JAVASCRIPT SAVED AS RUBY STRINGS)
cssFilePath = "https://raw.githubusercontent.com/dcts/remove-CSS-animations/master/css/remove.css"
js_arr = []
js_arr << "const linkElement = \"<link rel='stylesheet' type='text/css' href='#{cssFilePath}'>\";"
js_arr << "const head = document.querySelector('html > head');"
js_arr << "head.insertAdjacentHTML(\"beforeend\", linkElement);"
@driver.script(js_arr.join(""));
```

Step 4 can also be written in one line:
```ruby
# 4. disable animations (ONE-LINER)
@driver.script("document.querySelector('html > head').insertAdjacentHTML(\"beforeend\", \"<link rel='stylesheet' type='text/css' href='https://raw.githubusercontent.com/dcts/remove-CSS-animations/master/css/remove.css'>\");");
```

