<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <h2>Article Component</h2>
    <h3>{{ title }}</h3>
    <h2>Likes : {{ likes }} is publised : {{ isPublished ? 'Yes' : 'no'}}</h2>
  </div>
</template>

<script>
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Article',
    props: {
        title: String,
        likes: Number,
        isPublished : Boolean
    }
};
</script>

<style scoped></style>
