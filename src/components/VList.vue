<template>
        <li @dblclick="isEdit = true"


            :class="['list-group-item d-flex justify-content-between align-items-center created',{'deleted':isDelete}]">

            <!-- eslint-disable -->
            <input v-if="isEdit" @keyup.enter="isEdit = false" type="text" class="form-control" v-model="history.text">
            <div v-else class="form-check"  >
                <input v-model="history.isDone" class="form-check-input" type="checkbox" value="" :id="'customCheck'+history.id">
                <label :class="['form-check-label',{'done':history.isDone}]" :for="'customCheck'+history.id" >
                    {{history.text}}
                </label>
            </div>
            <div class="ml-5">
                <!-- <button @click="edi(history.id)" class="btn btn-sm text-info border">Edit</button> -->
                <i @click="[isDelete = true,del(history.id)]" class="p-2 text-danger border">Delete</i>
            </div>
            <!-- eslint-enable -->
        </li>
</template>

<script>
    export default {
        name: "VList",
        props:{
            history:{
                type: Object,
                required:true,
            }
        },
        data() {
            return {
                isEdit: false,
                isDelete: false,
            }
        },
        methods: {
            del(x) {
                this.$emit("del",x)
                console.log(x)
            }
        },
    }
</script>

<style scoped>

</style>