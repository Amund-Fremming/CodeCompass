# Firestore

## CRUD

**Imports you need**
```js
import { addDoc , collection, getDocs, deleteDoc, doc, updateDoc, onSnapshot } from "firebase/firestore";
import { db } from "./firebase";
import { v4 } from "uuid";
```

**Add db in firebase.js**
```js
export const db = getFirestore(app);
```

***Create***
```js
const createDoc = async () =>  {
    const id = v4(); // uuid library
    const todosRef = collection(db, "todos");
    await addDoc(todosRef, {
        // Object to add
    });
}
```

***Read***
```js
const getDoc = async () => {
    const docRef = collection(db, "todos");
    const rawData = await getDocs(docRef);
    const data = rawData.docs.data();
}
```

***Update***
```js
const updateDoc = async (id, newDoc) => {
    const document = doc(db, "<collection name>", id);
    await updateDoc(document, {
        // updated object
    });
}
```

***Delete***
```js
const deleteDoc = async (id) => {
    const document = doc(db, "<collection name>", id);
    await deleteDoc(document);
}
```