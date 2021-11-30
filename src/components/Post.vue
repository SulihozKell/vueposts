<template>
    <div>
        <PostItem
          v-for="post in posts"
          v-bind:key="post.title"
          :post="post"
          @selected-post-changed="Changed"
          />
    </div>
</template>

<script>
import PostItem from "./PostItem.vue"
export default {
    props: ["posts"],
    components: {PostItem},
    methods: {
        Changed(e) {
            this.$emit("selected-title-changed", e)
            this.$emit("selected-body-changed", e)
        }
    }
}
</script>
