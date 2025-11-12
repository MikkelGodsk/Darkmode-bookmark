# Darkmode-bookmark
This repo contains a simple bookmark you can add to your web browser to enable colour inversion for PDF files to help with eye strain while reading.

All you need to do is to create a bookmark and paste this as the URL:
```js
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
When you're viewing a PDF file, click the bookmark to execute the colour inversion.

I've tested it on the following browsers:
- On PC: Chrome, Edge, Firefox
- On iOS: Brave, Safari, Firefox


A more elaborate bookmark (it seems to work on most browsers including Firefox on PC, but not Firefox on iOS):
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
