<template>
<li v-for="i in paramList" :key="i.id">
<label><input v-model="i.isDone" type="checkbox"> {{ i.title }}</label>
</li>
</template>

<script>
export default {
    props:['paramList']
}
</script>

<style>
li {
  margin-bottom: 5px;
}
</style>