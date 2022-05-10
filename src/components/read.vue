<template>
    <div class="read">
        <div class="mt-1" v-for="blog in blog" :key="blog._id">
            <h4 class="card-title">{{ blog.title }}</h4>
            <div>
                <a href="/" class="btn btn-secondary">Back</a>
                <a href="/update-blog" class="btn btn-warning" id="update">Update</a>
            </div>
            <h5 class="card-subtitle">{{ blog.desc }}</h5>
            <h5 class="card-subtitle">{{ blog.mkdown }}</h5>
            <router-link :to="{name: 'edit', params: { id: blog._id }}" class="btn btn-warning">Update</router-link>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            blog: []
        }
    },
    created() {
        let apiURL = 'http://localhost:4000/api/';
        axios.get(apiURL).then((res) => {
            this.blog = res.data;
        }).catch(error => {
            console.log(error)
        })
    },
    methods: {
        deleteBlog(id) {
            let apiURL = 'http://localhost:4000/api/delete-blog/$(id)';
            let indexOfArrayItem = this.blog.findIndex(i => i._id === id);
            if (window.confirm("Confirm Delete")) {
                axios.delete(apiURL).then(() => {
                    this.blog.splice(indexOfArrayItem, 1);
                }).catch(error => {
                    console.log(error)
                })
            }
        }
    }
}
</script>

<style scoped>
    .read {
        max-width: 800px;
        margin: 0 auto;
    }

     #update {
        color: white;
    }
</style>