<template>
    <li>
        <div v-if="!edit">
            <h2>{{title}}<button @click="Edit">Edit</button></h2>
            <div>{{body}}</div>
        </div>
        <div v-if="edit">
            <input type="text" v-model="title">
            <input type="text" v-model="body">
            <button @click="Save">Save</button>
        </div>
    </li>
</template>

<script>
export default {
    props: ["post"],
    data() {
        return {
            title: this.post.title,
            body: this.post.body,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit("selected-post-changed", {
                original: this.post,
                new: {
                    title: this.title
                },
            }),
            this.$emit("selected-body-changed", {
                original: this.post,
                new: {
                    body: this.body
                },
            })
        }
    }
}
</script>
