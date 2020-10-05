# YouTube Unsubscriber

## Features
A Script to mass unsubscribe from all YouTube Channels you've already subscribed to.

## Browser compatibility
Supported in effectively all browsers.

## Steps
1. Go to [YouTube Channel List](https://www.youtube.com/feed/channels) to view a list of all the channels you've subscribed to.
2. Scroll down the bottom of the list. This script can only remove channels that are currently visible in the list.
3. Right Click and select **Inspect Element**. (or push Ctrl+Shift+I)
4. Go to **Console** and Paste the following content.

```
function unsub() {
    var els = document.getElementById("grid-container").getElementsByClassName("ytd-expanded-shelf-contents-renderer");
    if (els.length > 0) {
        let btn = els[0].querySelector("[aria-label^='Unsubscribe from']");
	btn.click();
	btn.scrollIntoView();
        setTimeout(function () {
            var unSubBtn = document.getElementById("confirm-button");
            els[0].parentNode.removeChild(els[0]);
            unSubBtn.click();
	    unsub()
        }, 200);
    } else {
	console.log("all done");
    }
}
unsub()
```
