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

***Query a documentRef***
```js
const getDocumentRef = async (<entry_to_search>) => {
    const collectionRef = collection(db, "<collection_name>");
    const q = query(collectionRef, where("<name_of_entry_in_collection>", "==", <entry_to_search>));
    try {
        const querySnapshot = await getDocs(q);
        if(!querySnapshot.empty) {
            const documentRefLocal = doc(collectionRef, querySnapshot.docs[0].id);
            setDocumentRef(documentRefLocal);
        }
    } catch(err) {
        console.log(err.message);
    }
};
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

***Read all***
```js
const getDoc = async () => {
    const docRef = collection(db, "todos");
    const rawData = await getDocs(docRef);
    const data = rawData.docs.data();
}
```

***Read one by id***
```js
const readDocById = async (collectionName, documentId) => {
    const documentRef = doc(db, collectionName, documentId);

    try {
        const docSnapshot = await getDoc(documentRef);

        if (docSnapshot.exists()) {
            const data = docSnapshot.data();
            console.log("Read document data: ", data);
            return data;
        } else {
            console.log("Document does not exist.");
            return null;
        }
    } catch (err) {
        console.log("Error: " + err.message);
    }
};
```

***Read one by field***
```js
const readDocByCustomField = async (collectionName, fieldName, fieldValue) => {
    const todosRef = collection(db, collectionName);
    const q = query(todosRef, where(fieldName, "==", fieldValue));

    try {
        const querySnapshot = await getDocs(q);

        if (!querySnapshot.empty) {
            // There may be multiple documents with the same field value,
            // but we'll return the data of the first matching document here.
            const firstDoc = querySnapshot.docs[0];
            const data = firstDoc.data();
            console.log("Read document data: ", data);
            return data;
        } else {
            console.log("No document matching the field value found.");
            return null;
        }
    } catch (error) {
        console.error("Error reading document by custom field: ", error);
        throw error; // You can handle the error as needed
    }
};
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


