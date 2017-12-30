!!! tip
    It's recommended to take a look at the firebase storage docs, please check the following link [firebase storage docs](https://firebase.google.com/docs/storage/web/start).

Myfirebase provides a simple way to interact with firebase storage via a global instance called `$storage`.

#### Myfirebase Storage instance

Syntax : `$storage`

`$auth` is a global auth instance which called through Vue component.

<hr>

#### Get firebase storage instance

Syntax : `$storage.get()`

You can retrieve firebase storage object using `get()` method.

<hr>

#### Get File URL

Syntax : `$storage.getDownloadURL(object)`

You can get your file URL of the user avatar or document which stored through firebase storage using `getDownloadURL`.

##### Example

```html
<template>
    <div class = "container">
        <img :src="avatar" alt="user-avatar" />
    </div>
</template>
<script>
    export default {
        mounted() {
            // Get file URL from firebase storage
            this.$storage.getDownloadURL({
                ref: "images/default.png",
                result: (result) => {
                    this.avatar = result
                },
                error: (error) => {
                    console.log(error.message)
                }
            })
        },
        data() {
            return {
                avatar: ""
            }
        }
    }
</script>
```

<hr>

#### Upload file

Sytax : `$storage.upload(object)`

You can upload a file to firebase cloud storage using `upload(object)`.

##### Example

We are going to upload a new file to the server using upload method.

```html
<template>
    <div class = "container">
        <label class="btn btn-default">
            <input type="file" class="hidden" @change="getFile">
            Browse
        </label>
        <button class="btn btn-primary" @click="uploadAvatar()"> update</i></button>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                // new file
                newAvatar: ""
            }
        },
        methods: {
            // get file form input
            getFile(e) {
                this.newAvatar = e.target.files[0]
            },
            // upload file
            uploadAvatar() {
                if (!this.newAvatar) {
                    return
                }
                let name = this.newAvatar.name
                // start uploading
                this.$storage.upload({
                    ref: `/images/${name}`,
                    file: this.newAvatar,
                    progress: (snapshot) => {},
                    error: (err) => {
                        console.log(err.message)
                    },
                    completed: (downloadURL) => {
                        console.log(downloadURL)
                    }
                })
            }
        }
    }
</script>
```

#### Delete file

Syntax : `$storage.delete(string)`

You can delete a file with `delete` method specifying the file path.

> The file's path is a storage path where the concerned file is located.

##### Example

```html
<template>
    <div class = "container">
        <button @click="delete()">Delete photo</button>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                file: "image/file.png"
            }
        },
        methods: {
            delete() {
                this.$storage.delete({
                    ref: this.file,
                    result: () => {
                        console.log("Deleted")
                    },
                    error: (error) => {
                        console.log(error.message)
                    }
                })
            }
        }
    }
</script>
```