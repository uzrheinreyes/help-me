<template>
    <div class="update">
        <img :src="logo" class="logo">
        <h1 class="title">Update Blog</h1>
        <form @submit.prevent = handleUpdateForm>
        <div class="form-group">
            <label for="file" class="image">Choose a photo +</label><br>
            <input type="file" id="file" accept="image/*"><br>

            <label for="title" class="mt-4">Title</label>
            <input required type="text" name="title" id="title" class="form-control" v-model="blog.title">

            <label for="description">Description</label>
            <textarea required name="description" id="description" class="form-control" v-model="blog.desc"></textarea>

            <label for="markdown">Markdown</label>
            <textarea required type="text" name="markdown" id="markdown" class="form-control" v-model="blog.mkdown"></textarea>
        </div>
        </form>
        <a href="/" class="btn btn-secondary mt-4">Cancel</a>
        <button class="btn btn-success mt-4">Save</button>
    </div>
</template>

<script>
import axios from 'axios';
export default ({
    data() {
        return {
            blog: { },
            logo: require('../assets/odyssey-logo.png')
        }
    },
    created() {
        let apiURL = 'http://localhost:4000/api/edit-blog/${this.$route.params.id}';

        axios.get(apiURL).then((res) => {
            this.blog = res.data;
        })
    },
    methods: {
        handleUpdateForm() {
            let apiURL = 'http://localhost:4000/api/update-blog/${this.$route.params.id}'

            axios.put(apiURL, this.blog).then((res) => {
                console.log(res)
                this.$router.push('/view')
            }).catch(error => {
                console.log(error)
            });
        }
    }
})
</script>

<style scoped>
    .logo {
        position: absolute;
        z-index: -1;
        width: 700px;
        margin: 50px 400px;
    }

    .update {
        max-width: 800px;
        margin: 100px auto;
    }

    input[type="file"] {
        display: none;
    }

    .image {
        color: white;
        height: 40px;
        width: 150px;
        background-color: rgb(212, 212, 86);
        display: flex;
        justify-content: center;
        align-items: center;
        margin: auto;
        border-radius: 6px;
        cursor: pointer;
        position: absolute;
        margin-top: 20px;
    }
</style>