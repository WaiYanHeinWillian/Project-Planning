<template>
  <nav class="filter-nav">
    <button @click="filterNav('all')" :class="{active:curNavRe==='all'}">All</button>
    <button @click="filterNav('complete')" :class="{active:curNavRe==='complete'}">Complete</button>
    <button @click="filterNav('ongoing')" :class="{active:curNavRe==='ongoing'}">Ongoing</button>
  </nav>
</template>

<script>
export default {

    props:['curNavRe'],

    methods:{
        filterNav(value){
            this.$emit('filterNavData',value)
        }
    }
}
</script>

<style>
    .filter-nav button{
        background: none;
        border: none;
        color: #bbb;
        outline: none;
        font-size: 12px;
        text-transform: uppercase;
        margin-right: 10px;
        letter-spacing: 1px;
        font-weight: bold;
        cursor: pointer;  
    }
    button.active{
        color: #333;
    }
</style>