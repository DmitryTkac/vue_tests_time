<template>
    <div id="calendar">
        <div>
            <h1>Today: {{ getTodayDate() }} </h1>
        </div>
        <ul>
            <li v-bind:key="calendarParts" v-for="calendarParts in calendarParts" v-on:click="changeStatus(calendarParts)">
                <h3 >
                    <span id="day"> {{ calendarParts.partName }} </span>:
                    <span> {{ calendarParts.partValue }} </span> |
                    <span v-show="calendarParts.showDescr"> {{ calendarParts.partDescription }} </span> 
                                 
                </h3>
                <button v-on:click="incValue(calendarParts)">Incrase Value</button>      
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "Calendar",
    props: {
        calendarParts: {
            type: Array
        }
    },
    
    
    methods: {
        changeStatus: function(part) {
            part.showDescr = !part.showDescr;
            //console.log("YOU CLICKED CHANGESTATUS() AAAAAAAAAAAA!" + part.showDescr);
        },

        incValue: function(part) {
            if (part.partName === "Day") {
                //console.log("This is a DAY!");
                if (part.partValue === 31) {
                    part.partValue = 1;
                    this.calendarParts[1].partValue++;
                    return;
                }
            } else if (part.partName === "Month") {
                if (part.partValue === 12) {
                    part.partValue = 1;
                    return;
                }
            }
            part.partValue++;
        },

        getTodayDate: function () {
            return new Date(Date.now());
        }
    }
}
</script>

<style scoped>
    h3 {
        background: #e2e5e6;
        width: 400px;
        height: 50px;
        margin: auto auto 20 auto;
        padding: 10px 10px 30px 10px;
        text-align: left;
    }

    #day {
        color: deepskyblue;
    }
    
    ul {
        list-style: none;
    }

    li {
        flex: 50%;
    }

    #calendar {
        background: #d0d3d4;
        width: 500px;
        margin: auto;
        padding: 20px;
        border-radius: 20px;
        box-shadow: 10px 5px;
    }
</style>


