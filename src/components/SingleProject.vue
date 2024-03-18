<template>
    <div class="project">
        <div class="flexing">
            <div>
                <h3 v-on:click="showDetailFun">{{projectly.title}}</h3>
            </div>
            <div>
                <span class="material-icons">
                 delete
                </span>
                <span class="material-icons">
                 edit
                </span>
                <span class="material-icons">
                 done
                </span>     
            </div>
        </div>
        <p v-if="showDetail">{{projectly.detail}}</p> 
    </div>
</template>

<script>
export default {
    props:['projectly'],

    data(){
        return{
            showDetail:false,
        }
    },

    methods:{
        showDetailFun(){
            return this.showDetail=!this.showDetail
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
</style>