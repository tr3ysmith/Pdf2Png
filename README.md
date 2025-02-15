# Pdf2PNG (Typescript Support)


## Install
```
npm install pdf2png-ts
```


This is based on another project. (https://github.com/Inkognitoo/Pdf2Png)

This version uses typescript and promises to greatly simplify usage since the old module is almost 7 years old.

---
## Setup
### Windows
No additional setup is needed for Windows, ghostscript is included with this package

### Linux
If you want to use it with linux, you will need to install ghostscript via your package manager.
~~~
> sudo apt-get update
> sudo apt-get install ghostscript
~~~

### Mac OSX
You will need to install ghostscript on mac using brew
~~~
brew install ghostscript
~~~

---
## Examples
here some examples how to use:

```typescript

// Create a PDFConvert Object to use for the each pdf file
// Buffer
const pdfConverter = new PDFConvert(buffer);
// OR web url
const pdfConverter = new PDFConvert("http://example.com/example.pdf");

// Get the page count of the PDF (this returns a promise)
const pages = await pdfConverter.getPageCount()

// Get page 1 as a PNG Image Buffer
const buffer = await pdfConverter.convertPageToImage(1)
await fs.writeFile("example_page1.png", buffer);

/**
 * Make sure you always clean the converter object when you're done using it, 
 * Otherwise the pdf tmp file will not be removed.
 * 
 * Having to manually call clean allows you to run multiple operations on the same tmp file
 * and reduces latency with having to refetch and write the pdf to a tmp location on every
 * call.
 */
pdfConverter.clean()

```