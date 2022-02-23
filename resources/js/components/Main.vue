<template>
    <main>
        <div class="container">
        <h2>Lista posts</h2>
        <ul class="posts">
            <li class="post-container" v-for="post in posts" :key="post.id">
                <h3>{{post.title}}</h3>
                <p>{{post.content}}</p>
                <div class="categories">
                    <strong>Categoria: </strong>
                    <span v-for="(category, index) in post.category_id" :key="index">{{category}}</span>
                </div>
            </li>
        </ul>

        </div>
    </main>
</template>

<script>
export default {
    name: 'Main',
    data() {
        return {
            posts: []
        }
    },
    created() {
        axios.get("/api/posts")
            .then((response) => {
                this.posts = response.data;
            })
            .catch((error) => {
                console.log(error);
            });
    }
}
</script>

<style lang="scss" scoped>
.container {
    width: 1200px;
    margin: 0 auto;
    h2 {
        text-align: center;
        margin: 20px 0 20px 0;
    }
    .posts {
        list-style: none;
        .post-container {
            background-color: #aaa;
            border-radius: 15px;
            padding: 15px;
            margin-top: 20px;
            h3 {
                text-align: center;
            }
            p {
                padding: 15px;
            }
            .categories {
                padding: 15px;
            }
        }
    }

}
</style>