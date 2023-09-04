# Firestore

## CRUD

**Imports you need**

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