<template>
    <div id="Time">
        <h1>This will be time | By {{ nickname }}</h1>
        <hr>
        <div id="timeBlock">
            <h2>Time information: TODAY</h2>
            <div id="infoBlock">
                YEAR: {{ getYearFromDate(getTodayFromDate()) }}
            </div>
            <div id="infoBlock">
                MONTH: {{ getMonthFromDate(getTodayFromDate()) }}
            </div>
            <div id="infoBlock">
                DAY: {{ getDayFromDate(getTodayFromDate()) }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Time",

    props: {
        nickname: String
    },

    methods: {

        getTodayFromDate: function() {
            return new Date(Date.now());
        },

        getYearFromDate: function(date) {
            return date.getFullYear();
        },

        getMonthFromDate: function(date) {
            return ("0" + String(date.getMonth() + 1)).slice(-2);
        },

        getDayFromDate: function(date) {
            return ("0" + String(date.getDate())).slice(-2);
        }

    }
    
}
</script>

<style scoped>
    hr {
        width: 50%;
        margin: auto;

        margin-bottom: 50px;
    }

    #timeBlock {
        width: 600px;
        height: 700px;
        margin: auto;
        background: #d0d3d4;
        border-radius: 20px;
        box-shadow: 10px 5px;
    }

    #infoBlock {
        color: white;
        width: 90%;
        margin: auto;
        background: #8d8e8f;
        border-radius: 15px;
        font-size: 15pt;
        margin-top: 20px;        
    }
</style>


