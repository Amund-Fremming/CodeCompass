# CRUD

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
const getDocumentRef = async (entry_to_search) => {
    const collectionRef = collection(db, "<collection_name>");
    const q = query(collectionRef, where("<name_of_entry_in_collection>", "==", entry_to_search));
    try {
        const querySnapshot = await getDocs(q);
        if(!querySnapshot.empty) {
            // Set your local states
        }
    } catch(err) {
        console.log(err.message);
    }
};
```

***Create***
```js
const createDoc = async () =>  {
    try {
        const id = v4(); // uuid library
        const todosRef = collection(db, "todos");
        await addDoc(todosRef, {
            // Object to add
        });
    } catch (err) {
        console.log("Error: " + err.message);
    }
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
const readDocByCustomFieldUsingRef = async (collectionName, fieldName, fieldValue) => {
    try {
        const documentRef = await getDocumentRef(fieldValue, collectionName);
        if (documentRef) {
            const docSnapshot = await getDoc(documentRef);

            if (docSnapshot.exists()) {
                const data = docSnapshot.data();
                console.log("Read document data: ", data);
                return data;
            } else {
                console.log("Document does not exist.");
                return;
            }
        } else {
            console.log("No document matching the field value found.");
            return null;
        }
    } catch (error) {
        console.error("Error reading document by custom field using reference: ", error);
        throw error; // You can handle the error as needed
    }
};
```

***Update by id***
```js
const updateDoc = async (id, newDoc) => {
    const document = doc(db, "<collection name>", id);
    await updateDoc(document, {
        // updated object
    });
}
```

***Update by field***
```js
const updateDocByField = async (entryName, newData) => {
    try {
        // See method on top of page
        const documentRef = await getDocumentRef(entryName);

        if (documentRef) {
            const docSnapshot = await getDoc(documentRef);

            if (docSnapshot.exists()) {
                // Update your data
                // const updatedData
                await updateDoc(documentRef, updatedData);
                console.log("Document updated successfully.");
            } else {
                console.log("Document does not exist.");
            }
        } else {
            console.log("No document matching the entry name found.");
        }
    } catch (error) {
        console.error("Update operation failed: ", error);
    }
};

```

***Delete by field***
```js
const deleteDoc = async (id) => {
    const document = doc(db, "<collection name>", id);
    await deleteDoc(document);
}
```

***Delete by field***
```js
const deleteDocByField = async (entryName) => {
    try {
        // See method on top of page
        const documentRef = await getDocumentRef(entryName);

        if (documentRef) {
            const docSnapshot = await getDoc(documentRef);

            if (docSnapshot.exists()) {
                await deleteDoc(documentRef);
                console.log("Document deleted successfully.");
            } else {
                console.log("Document does not exist.");
            }
        } else {
            console.log("No document matching the entry name found.");
        }
    } catch (error) {
        console.error("Delete operation failed: ", error);
    }
};
```


