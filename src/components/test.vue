<template>
    <div class="main">
        <h1>THERE WILL BE SOMETHING INTERESTING</h1>
        <div id="itemBox">
            <h2>ITEM BOX</h2>
            <div id="jflex">
                <week v-bind:key="week" v-for="week in 35" ></week>
                
            </div>
            
        </div>
    </div>
</template>

<script>
import week from './week.vue';

export default {
    name: "test",

    components: {
        week
    }
}
</script>

<style scoped>

    #jflex {
        display: flex;
    }

    .main {
        width: 1000px;
        min-height: 600px;
        margin: 20px auto 0 auto;
        background: #d0d3d4;
        border-radius: 20px;
        box-shadow: 10px 5px;
        color: #ce4141;
    }   

    #itemBox {
        width: 800px;
        min-height: 200px;
        background: #e2e2e2;
        margin: 20px auto 0 auto;
        box-shadow: 100px 10px 1000px 900px rgba(133, 133, 133, 0.377);
        border: 2px solid lightsteelblue;
        
    }
</style>



