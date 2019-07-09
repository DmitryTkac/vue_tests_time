<template>
    <div id="Time">
        <h1>This will be time test | By {{ nickname }}</h1>
        <hr>
        <div id="timeBlock">
            <h2>Time information: {{ timeInfoTitle }} </h2>
            <div id="infoBlock">
                YEAR: {{ timePart.year }}
            </div>
            <div id="infoBlock">
                MONTH: {{ timePart.monthName }}
            </div>
            <div id="infoBlock">
                DAY: {{ timePart.day }}

            </div>
            <div id="infoBlock">
                WEEKDAY: {{ timePart.weekday }}
            </div>
            <div id="infoBlock">
                TIME: {{ getTimeFromDate(getTodayFromDate()) }}
            </div>
            <div id="dataPick">
                <h3>v-model datepicker</h3>
                <datepicker placeholder="Select Date" v-model="timeUpdater"></datepicker>
                <button v-on:click="updateTimeInfoTable" >UPDATE</button>
                <hr/>
                <p>THERE: {{ timeUpdater }}</p>
            </div>

            <div id="weekday"> 
                <div>{{ timePart.weekday }}</div>
                <div> {{ timePart.weekday }}</div>
             </div>
             <div id="flexed">
                <div id="oneDayBlock">
                    <span> {{ timePart.monthName }} </span>
                    <br>
                    <span id="day"> {{ timePart.day }} </span>                
                </div>
                <br>
                <div id="oneDayBlock">
                    <span> {{ timePart.monthName }} </span>
                    <br>
                    <span id="day"> {{ this.nextDay }} </span>                
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import Datepicker from 'vuejs-datepicker';
export default {
    name: "Time",

    data() {
        return {
            timeInfoTitle: "Today",
            timePart: {
                year: this.getYearFromDate(this.getTodayFromDate()),
                month: this.getMonthFromDate(this.getTodayFromDate()),
                monthName: this.getMonthName(this.getMonthFromDate(this.getTodayFromDate())),
                day: this.getDayFromDate(this.getTodayFromDate()),
                weekday: this.getWeekDayFromDate(this.getTodayFromDate()),               
            },
            timeUpdater: "AAAAaaaa..??",
            nextDay: parseInt(this.getDayFromDate(this.getTodayFromDate()))+1
        }
    },

    props: {
        nickname: String,
        
    },
    
    components: {
        Datepicker
    },

    methods: {

        getTodayFromDate: function() {
            return new Date(Date.now());
        },

        getYearFromDate: function(date) {
            return date.getFullYear();
        },

        zeroPadding: function(value) {
            return value < 10? ("0"+String(value)).slice(-2) : String(value).slice(-2);
        },

        getMonthFromDate: function(date) {
            return date.getMonth();
        },

        getMonthName: function(monthValue) {
            let month = ["JAN", "FEB", "MAR", "APR", "MAY", "JUN", "JUL", "AUG", "SEP", "OCT", "NOV", "DEX"];   
            return month[monthValue];            
        },  

        getDayFromDate: function(date) {
            let day = date.getDate()
            return this.zeroPadding(day);
        },

        getHourFromDate: function(date) {
            let hour = date.getHours();
            return this.zeroPadding(hour);
        },

        getMinutesFromDate: function(date) {
            let minutes = date.getMinutes();
            return this.zeroPadding(minutes);
        },

        getSecondsFromDate: function(date) {
            let seconds = date.getSeconds();
            return this.zeroPadding(seconds);
        },

        getTimeFromDate: function(date) {
            return this.getHourFromDate(date) + ":" + this.getMinutesFromDate(date) + ":" + this.getSecondsFromDate(date);
        },

        getWeekDayFromDate: function(date) {
            let weekday = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturady"];
            return weekday[date.getDay()];
        },

        updateTimeInfoTable: function() {
            
            this.timePart.year = this.getYearFromDate(this.timeUpdater);
            this.timePart.month = this.getMonthFromDate(this.timeUpdater);
            this.timePart.monthName = this.getMonthName(this.timePart.month);
            this.timePart.day = this.getDayFromDate(this.timeUpdater);
            this.timePart.weekday = this.getWeekDayFromDate(this.timeUpdater);
            //this.nextDay = (Date.parse(this.timeUpdater));
            this.timeInfoTitle = new Date(this.timePart.year, 10, this.timePart.day);
            this.nextDay = this.timePart.day;
            this.nextDay++;
        },

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
        height: 900px;
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

    #dataPick {
        width: 80%;
        margin: auto;
    }

    #dataPick hr {
        margin-top: 10px;
        margin-bottom: 10px;
    }

    #oneDayBlock {
        width: 80px;
        padding: 20px;
        margin: auto;
        background: white;
        border-color: black;
        border: 5px solid;
        border-radius: 10px;
        
    }

    #day {
        font-size: 50pt;
    }

    #weekday {
        background: lightslategray;
        color: white;
        width: 80%;
        margin: 0% auto 20px auto;
        display: flex;
    }

    #weekday div {
        width: 300px;
    }

    #flexed {
        display: flex;
    }
</style>


