<template>
    <div class="project" :class={completeColor:this.projectly.complete}>
        <div class="flexing">
            <div>
                <h3 v-on:click="showDetailFun">{{projectly.title}}</h3>
            </div>
            <div>
                <span class="material-icons" @click="deleteProject">
                 delete
                </span>

                <router-link :to="{name:'EditProject',params:{id:projectly.id}}">
                    <span class="material-icons">
                    edit
                    </span>
                </router-link>

                <span class="material-icons" v-on:click="completeProject">
                 done
                </span>     
            </div>
        </div>
        <p v-if="showDetail">{{projectly.detail}}</p> 
        {{this.projectly.complete}}
    </div>
</template>

<script>
export default {
    props:['projectly'],

    data(){
        return{
            showDetail:false,
            api:'http://localhost:3000/projects/',
        }
    },

    methods:{
        showDetailFun(){
            return this.showDetail=!this.showDetail
        },
        deleteProject(){
            let dleteApiPj=this.api+this.projectly.id;
            fetch(dleteApiPj,{method:"DELETE"})
            .then(()=>{
                this.$emit("deleting",this.projectly.id)
            })
            .catch((err)=>{
                console.log(err.message)
            })
        },
        completeProject(){
            let updCompRoute=this.api+this.projectly.id;
            fetch(updCompRoute,{
                method:"PATCH",
                headers:{
                    "Content-Type":"application/json"
                },
                body:JSON.stringify(
                    {
                        complete:!this.projectly.complete
                    }
                )
            })
            .then(()=>{
                this.$emit("updCompProj",this.projectly.id);
            })
            .catch((err)=>{
                console.log(err);
            })          
        }
    }
}
</script>

<style>
    .project{
        background-color: #f2f2f2;
        padding: 20px;
        margin: 10px;
        border-left: 7px solid crimson;
        border-radius: 10px;
        
    }
    h3{
        color: indigo;
        cursor: pointer;
    }
    .flexing{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    span{
        margin-left: 10px;
    }
    span:hover{
        color: #777;
        cursor: pointer;
    }
    .completeColor{
        border-left-color: green;
    }
</style>