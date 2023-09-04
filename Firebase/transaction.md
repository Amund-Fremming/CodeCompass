## Transactions CRUD

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

***Read***
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

***Update***
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

***Delete***
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



