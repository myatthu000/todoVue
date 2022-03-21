<template>
    <div class="">
        <div class="d-flex justify-content-center align-items-center">
            <input @keyup="showError = false" v-model="message" type="text" class="form-control mr-2">
            <button @click="add()" class="btn btn-primary">Add</button>
        </div>
        <div class="col-12">
            <small v-if="showError" class="text-danger">
                {{errorMessage}}
            </small>
        </div>
    </div>
</template>

<script>
    export default {
        name: "VListCreate",
        data() {
            return {
                message: "",
                showError: false,
                errorMessage : "",
            }
        },

        methods: {
            add() {
                // if (this.message == "" || this.message.length == 0){
                //     return {a:confirm("Type something ..."),b:false};
                // }else {
                //     this.$emit("addEve",this.message);
                //     this.message = "";
                // }
                if (this.message.length){
                    this.$emit("addEve",this.message);
                    this.message = "";
                    this.showError = false;
                }else {
                   this.showError = true;
                   this.errorMessage = "Say something"
                }

            }
        },
    }
</script>

<style scoped>

</style>