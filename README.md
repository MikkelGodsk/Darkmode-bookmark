# PDF-darkmode
To make a button that can enable PDF darkmode in your browser, create a bookmark and paste this code as your URL:
```
JavaScript:(
    function(){
        const htmlElement = document.documentElement; 
        const filter_str = "invert(1) contrast(75%) hue-rotate(180deg)"; 
        if (htmlElement.style.filter === filter_str) { 
            htmlElement.style.filter = ""; 
        } else { 
            htmlElement.style.filter = filter_str; 
        } 
    }
)(); 
```
I've tested it on the following browsers:
- On PC: Chrome, Edge, Firefox
- On iOS: Brave, Safari, Firefox
