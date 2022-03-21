<template>
    <div>
        <h3 class="text-center mb-3">
            {{todoTitle}}
        </h3>
    </div>
</template>

<script>
    export default {
        name: "VTitle",
        props:{
            todoTitle:{
                default:'Vue Js Todo List',
            }
        }
    }
</script>

<style scoped>

</style>