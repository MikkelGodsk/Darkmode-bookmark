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
```
javascript:(function(){
    const htmlElement = document.documentElement;
    const filter_str = "invert(1) hue-rotate(180deg) contrast(75%)";
    const media_filter_str = "invert(1) hue-rotate(180deg) contrast(133%)";
    const media_elements = document.querySelectorAll('img, svg, video');

    if (htmlElement.style.filter) {
        htmlElement.style.filter = "";
        media_elements.forEach(media => media.style.filter = "");
    } else {
        htmlElement.style.filter = filter_str;
        media_elements.forEach(media => media.style.filter = media_filter_str);
    }
})();
```
