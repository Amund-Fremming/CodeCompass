# Transactions CRUD

**Imports you need**
```js
import { runTransaction } from "firebase/firestore";
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
const createDoc = async () => {
    const id = v4(); // uuid library
    const todosRef = collection(db, "todos");
    
    try {
        await runTransaction(db, async (transaction) => {
            await addDoc(todosRef, {
                // Object to add
            });
        });
    } catch (error) {
        console.error("Transaction failed: ", error);
    }
};
```

***Read all***
```js
const getDoc = async () => {
    const docRef = collection(db, "todos");

    try {
        const data = await runTransaction(db, async (transaction) => {
            const rawData = await getDocs(docRef);
            return rawData.docs.map((doc) => doc.data());
        });

        console.log("Read data: ", data);
    } catch (error) {
        console.error("Transaction failed: ", error);
    }
};
```

***Read by id***
```js
const readDocByIdTransaction = async (id) => {
    try {
        const result = await runTransaction(db, async (transaction) => {
            const documentRef = doc(db, "todos", id);
            const docSnapshot = await getDoc(documentRef);

            if (docSnapshot.exists()) {
                const data = docSnapshot.data();
                console.log("Read document data: ", data);
                return data;
            } else {
                console.log("Document does not exist.");
                return null;
            }
        });

        return result;
    } catch (error) {
        console.error("Transaction failed: ", error);
        throw error; // You can handle the error as needed
    }
};
```

***Read by field***
```js

```

***Update with id***
```js
const updateDoc = async (id, newDoc) => {
    const document = doc(db, "todos", id);

    try {
        await runTransaction(db, async (transaction) => {
            await updateDoc(document, {
                // updated object
            });
        });
    } catch (error) {
        console.error("Transaction failed: ", error);
    }
};
```

***Update with given entry***
```js
const updateDocByField = async (entryName, newData) => {
    try {
        // See method on top of page
        const documentRef = await getDocumentRef(entryName);

        if (documentRef) {
            await runTransaction(db, async (transaction) => {
                const docSnapshot = await getDoc(documentRef);

                if (docSnapshot.exists()) {
                    // Update your data
                    // const updatedData;
                    await updateDoc(documentRef, updatedData);
                    console.log("Document updated successfully.");
                } else {
                    console.log("Document does not exist.");
                }
            });
        } else {
            console.log("No document matching the entry name found.");
        }
    } catch (error) {
        console.error("Transaction failed: ", error);
        throw error; // You can handle the error as needed
    }
};
```

***Delete with id***
```js
const deleteDoc = async (id) => {
    const document = doc(db, "todos", id);

    try {
        await runTransaction(db, async (transaction) => {
            await deleteDoc(document);
        });
    } catch (error) {
        console.error("Transaction failed: ", error);
    }
};
```

***Delete with given entry***
```js
const deleteDocByField = async (entryName) => {
    try {
        // See method on top of page
        const documentRef = await getDocumentRef(entryName);

        if (documentRef) {
            await runTransaction(db, async (transaction) => {
                const docSnapshot = await getDoc(documentRef);

                if (docSnapshot.exists()) {
                    // Delete the document
                    await deleteDoc(documentRef);
                    console.log("Document deleted successfully.");
                } else {
                    console.log("Document does not exist.");
                }
            });
        } else {
            console.log("No document matching the entry name found.");
        }
    } catch (error) {
        console.error("Transaction failed: ", error);
    }
};
```



