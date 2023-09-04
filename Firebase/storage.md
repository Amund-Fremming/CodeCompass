# Storage

**Imports you need**
```js
import { storage } from "../firebase";
```

***Upload image**
- This will return a url you can store in firestore database and use as a image in you application.
```js
const uploadImage = () => {
    return new Promise((resolve, reject) => {
        if(imageUpload == null) return;
        const imageRef = ref(storage, `images/${imageUpload.name + v4()}`)
        uploadBytes(imageRef, imageUpload).then(snapshot => {
            getDownloadURL(snapshot.ref).then(url => {
                resolve(url);
            })
        }).catch(error => {
            console.error("Failed to upload image:", error);
            reject(error);
        });
    });
}   
```