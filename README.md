# Boosty_chat_fix
1) устанавливаете [Tampermonkey](https://chromewebstore.google.com/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)
2) Нажимаете создать новый скрипт
3) Вставляете код ниже
```js
// ==UserScript==
// @name         BoostyFix
// @namespace    http://tampermonkey.net/
// @version      2024-10-15
// @description  Fix jumping chat on bossty
// @author       NeoDim
// @match        https://boosty.to/dawgonosik/streams/video_stream
// @icon         https://www.google.com/s2/favicons?sz=64&domain=boosty.to
// @grant        none
// ==/UserScript==

;(function() {
    setInterval(() => {
        const innerScrollContainer = document.querySelector('.ReactVirtualized__Grid__innerScrollContainer');

        let welcomeMessageFound = false;

        innerScrollContainer.childNodes.forEach(child => {
            if (child.nodeType === 1 && child.children.length > 0) {
                const grandChild = child.children[0];
                if (grandChild.textContent.trim() === 'Welcome to chat') {
                    welcomeMessageFound = true;
                }
            }
        });
        if (welcomeMessageFound) document.querySelector(".ChatBoxBase_scrollButton_zlsO4")?.click()
    }, 1000);
})()
```
4) Включаете скрипт и обновляете страницу
