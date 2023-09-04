# onSnapshot

**Imports you need**
```js
import { onSnapshot, collection, where, query } from 'firebase/firestore';
```

***Query a documentRef***
```js
const getDocumentRef = async (entry_to_search) => {
    const collectionRef = collection(db, "<collection_name>");
    const q = query(collectionRef, where("<name_of_entry_in_collection>", "==", entry_to_search));
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

***Listen to a given entry***
```js
useEffect(() => {
    const documentRef = getDocumentRef(entryName);

    const unsubscribe = onSnapshot(documentRef, snapshot => {
        if(snapshot.data()) {
            const data = snapshot.data();
            // Set the data to your states
        }
    });

    return () => unsubscribe(); 
}, [documentRef]);
```

***Listen to the collection***
```js
useEffect(() => {
    // Gets the whole collection
    const documentRef = collection(db, "<collection_name>");

    const unsubscribe = onSnapshot(documentRef, snapshot => {
        const data = snapshot.data();
        // Set the data to your states
    });

    // Return a cleanup function to unsubscribe when the component unmounts
    return () => {
        unsubscribe();
    };
}, []);
```