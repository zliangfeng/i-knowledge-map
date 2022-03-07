# Pdf generation

## references

- <https://blog.theodo.com/2021/10/pdf-generation-react-puppeteer/>

## contents

### 技术点

- Render a printable version of your page

```js
const tabNames = ['tab1', 'tab2', 'tab3']

(isPrintable
  ? tabNames.map(tabName => <Table key={tabName} selectedTab={tabName} /> 
  : <Table selectedTabIndex='tab1' />
);
```

- Deal with page breaks and fixed size with CSS

```CSS
media @print {
  body: {
    font-size: "16px";
    color: "lightgrey";
  }

  .no-break-inside {
    // apply this class to every component that shouldn't be cut off between to pages of your PDF
    break-inside: "avoid";
  }

  .break-before {
    // apply this class to every component that should always display on next page
    break-before: "always";
  }
}
```

- 服务端

```js
const puppeteer = require("puppeteer");

(async () => {
  const browser = await puppeteer.launch(); // launch a browser (chromium by default but you can chose another one)
  const page = await browser.newPage(); // open a page in the browser
  await page.goto("https://printable-version-of-my-wbe-page.com", {
    waitUntil: "networkidle2",
  }); // visit the printable version of your page
  await page.pdf({ format: "a4", path: "./my_file.pdf" }); // generate the PDF 🎉
  await browser.close(); // don't forget to close the browser. Otherwise, it may cause performances issues or the server may even crash..
})();
```
