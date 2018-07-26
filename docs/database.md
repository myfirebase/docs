Myfirebase provides a simple way to deal with the Firebase real-time database and Firestore.

For creating a new database model, you can run in your terminal `myfirebase new:model <model-name>`.

### How does it works?

Once you create a new model in the project, you will see somthing like this.

```javascript
import { FirestoreModel } from 'myfirebase'

class Person extends FirestoreModel {

    /**
     * Create new Person instance.
     * 
     * @param {*} ref
     */
    constructor (ref) {
        super(ref)
    }

    /**
     * Define required properties.
     * 
     * @return array
     */
    required () {
        return []
    }
}

export default Person;
```

Let say we've created a new component for managing users accounts.

It becomes easy for us to add/remove documents to our database, we can add the Person object in Vue data property, and then initialize the Person object with the database reference which might be a real-time reference or Firestore ones, Myfirebase model binds on Person properties.


We can add a new record to our database by:

`push()` - in case of using real-time database.

`add()` - in case of using Firestore database.

Example:


!!! info
    1 - You need to import the model into the component.

    `import Person from "@/models/Person"`

    2 - Then you have to initialize the model with `init()` in the vue's data property.

    ```
      data: () => {
        Person: new Person(database_ref).init()
      }
    ``` 

```html
<template>
  <div>
    <v-card>
      <v-list two-line subheader>
        <v-subheader>Persons</v-subheader>
        <v-list-tile v-for="(person, index) in data" :key="index">
          <v-list-tile-content>
            <v-list-tile-title>{{person.name}}</v-list-tile-title>
          </v-list-tile-content>
          <v-list-tile-action>
            <v-icon color="black" @click="deletePerson(person['.key'])">delete</v-icon>
          </v-list-tile-action>
        </v-list-tile>
      </v-list>
      <v-container>
      <v-text-field
      label="Person Name"
      v-model="Person.name"
      @keyup.enter="addPerson()"
      ></v-text-field>
      <v-btn @click="addPerson()">Add Person</v-btn>
      </v-container>
    </v-card>
    </div>
  </div>
</template>

<script>

import Person from "@/models/Person";

export default {
  mounted () {
      //
  },
  firebase () {
    return {
      data: {
        source: this.$store.state.database.child("persons"),
        readyCallback: () => {
        }
      }
    };
  },
  data () {
    return {
        // init the Person's db model.
      Person: new Person(this.$store.state.database.child('persons')).init(),
    }
  },
  methods: {
    addPerson () {
        // The record added automatically.
      this.Person.push()
    },
    deletePerson (key) {
      this.Person.remove(key);
    }
  }
};
</script>
```

You can also update or remove a document from the database.

Example:

```javascript
// delete document.
this.Person.delete(key)

// update document
this.Person.update(key)
```

### API

#### Firebase database.

Add JSON document.

```
Syntax: model.push()
return: Promise
```

Delete JSON document.

```
Syntax: model.remove(document_key)
return: Promise
```

Update JSON document.

```
Syntax: model.update(document_key)
return: Promise
```

#### Cloud Firestore.

Add JSON document.

```
Syntax: model.add()
return: Promise
```

Delete JSON document.

```
Syntax: model.delete(document_key)
return: Promise
```

Update JSON document.

```
Syntax: model.update(document_key)
return: Promise
```