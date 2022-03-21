<template>
    <div>
        <div class="container-fluid">
            <div class="row border p-3">
                <div class="mt-4 border">
                    <div class="p-3">
                        <VTitle todo-title="Vue Js Todo List"></VTitle>

                        <VListCreate @addEve="add"></VListCreate>

                        <div class="d-flex justify-content-between my-3">
                            <span v-if="histories.length > 0 && doneTotal == histories.length" class="badge rounded-pill bg-success">
                                All Done
                            </span>
                            <span v-else class="badge rounded-pill bg-info">
                                Done {{ doneTotal  }}
                            </span>

                            <span class="badge rounded-pill bg-warning">
                                Total list( {{histories.length }} )
                            </span>
                        </div>
                        <div class="mt-3">
                            <ul class="list-group ">

                                <VList v-for="history in histories" :key="history.id"
                                       :history="history" @del="del"
                                ></VList>

                                <li v-if="histories.length === 0" class="text-center list-group-item d-flex justify-content-center align-items-center">
                                    There is no List
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import VTitle from "@/components/VTitle";
    import VList from "@/components/VList";
    import VListCreate from "@/components/VListCreate";
    export default {
        name:"App",
        components: {VListCreate, VList, VTitle},
        data(){
            return{
                currentId:0,
                // message: "",
                histories:[],
                totalHistories:0,
            }
            //r:[{id:this.currentId,text:this.message}],
        },
        computed:{
            doneTotal(){

                let d = this.histories.filter(el=>el.isDone == true).length
                return d
            }
        },
        methods:{

            add:function(x){

                this.currentId++
                this.histories.push(
                    {
                        id:this.currentId,
                        text:x,
                        isDone: false,
                    }
                )
                // console.log(this.currentId)
                // this.message = "";

            },

            del:function(x){
                // this.histories = this.histories.filter(el=>el.id !== x)
                //if(confirm("Are you sure?")){
                setTimeout(()=>this.histories = this.histories.filter(el=>el.id !== x),500)
                // console.log(this.history)
                //}
            },

        },
    }
</script>

<style>
    .done{
        text-decoration: line-through !important;
        animation:0.5s shakeX !important;
    }
    .created{
        animation:0.5s fadeIn !important;
    }
    .deleted{
        animation:0.5s zoomOut !important;
    }
</style>