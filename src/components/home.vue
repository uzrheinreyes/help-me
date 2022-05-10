<template>
<div class="logo">
    <img :src="logotype" class="logotype">
    <div class="home">
        <div class="content">
            <h2 class="title">Your blogs</h2>
            <a href="/create-blog" class="btn btn-success mt-4">New Blog +</a>
            <div class="card mt-4">
                <div class="card-body">
                    <div id="card-content">
                        <div>
                            <img :src="pic1" class="pic1">
                        </div>
                        <div class="mt-1">
                            <h4 class="card-title">Title</h4>
                            <div class="card-subtitle text-muted mb-2">Description</div>
                        </div>
                    </div>
                    <div id="buttons" class="mt-2">
                        <a href="/read-blog" class="btn btn-primary">Read more</a>
                        <a href="/update-blog" class="btn btn-warning" id="update">Update</a>
                        <a href="/delete-blog" class="btn btn-danger">Delete</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data: function() {
        return {
            logotype: require('../assets/odyssey-logotype.png'),
            pic1: require("../assets/odyssey-home.jpg")
        }
    },
}
</script>

<style scoped>
    .logo {
        margin: 0 0 0 200px;
    }

    .home {
        max-width: 1000px;
        margin: 0 auto;
    }

    .logotype {
        width: 450px;
    }

    .pic1 {
        width: 250px;
        padding: 10px;
        display: inline-block;
        border-radius: 20px;
    }

    #buttons {
        display: block;
    }

    #card-content {
        display: flex;
    }

    #update {
        color: white;
    }

</style>
