# cordova-plugin-android-mediastore
This simple Cordova plugin converts a base64 `image/jpeg` bytestring to an image file and adds it to the gallery.

Tested on Android APIs 22(5.1 Lollipop), 29(10 Q) and 30(11 R).

Useful when capturing an HTML canvas.

## API
The plugin exports only one function:

```javascript
//CordovaAndroidMediaStore.js

/**
 * @param byteString the bytestring part of the base64 dataURI (excludes the MIME part, see the example)
 * @param fileDir the relative directory to save the file to.
 * @param fileName 
 */
exports.store = function (byteString, fileDir, fileName, success, error) {
    exec(success, error, 
        'CordovaAndroidMediaStore', 
        'store', 
        [byteString, fileDir, fileName]);
};
```

## example
```typescript
let byteString = dataURI.split(",")[1];
cordova.plugins.CordovaAndroidMediaStore.store(byteString, "Pictures", `${Date.now()}.jpg`);
```
