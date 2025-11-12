# Darkmode-bookmark
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


A more elaborate bookmark that'll also work on websites while preserving the images (although there will be some loss of colour vibrancy):
```js
javascript:(function() {
    document.documentElement.classList.toggle('dark-mode-bookmarklet');
    if (!document.getElementById('dark-mode-bookmarklet-style')) {
        var style = document.createElement('style');
        style.id = 'dark-mode-bookmarklet-style';
        style.textContent = `
            .dark-mode-bookmarklet {
                filter: invert(1) hue-rotate(180deg) contrast(75%);
                background-color: #fefefe;
            }
            .dark-mode-bookmarklet img,
            .dark-mode-bookmarklet video,
            .dark-mode-bookmarklet iframe,
            .dark-mode-bookmarklet svg {
                filter: invert(1) hue-rotate(180deg) contrast(133%);
            }
        `;
        document.head.appendChild(style);
    }
})();
```
