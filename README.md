# PDF-darkmode
This repo contains a simple bookmark you can add to your web browser to enable colour inversion for PDF files to help with eye strain while reading.

All you need to do is to create a bookmark and paste this as the URL:
```
JavaScript:(
    function(){
        const htmlElement = document.documentElement; 
        const filterStr = "invert(1) contrast(75%) hue-rotate(180deg)"; 
        if (htmlElement.style.filter === filterStr) { 
            htmlElement.style.filter = ""; 
        } else { 
            htmlElement.style.filter = filterStr; 
        } 
    }
)(); 
```
When you're viewing a PDF file, click the bookmark to execute the colour inversion.

I've tested it on the following browsers:
- On PC: Chrome, Edge, Firefox
- On iOS: Brave, Safari, Firefox
