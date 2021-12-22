<template>
    <div>
        <GChart class="chart" type="ColumnChart" :options="options" :data="data" />  
    </div>
</template>

<script>
import { GChart } from "vue-google-charts";

export default {
    name: "Chart",
    components: {
        GChart
    },
    props: [
        "items"
    ],
    data() {
        return {
            data: [],
            options: {
                width: "80%",
                height: 400,
                bars: 'horizontal',
                legend: {position: 'none'}
            }
        }
    },
    mounted() {
        this.createChartData();
        //while(true) {
                //this.weenRuben();
        //}
    },
    methods: {

        createChartData(){

            let data = []
            data.push(["Title", "Points"]);

            console.log(this.items);

            this.items.forEach(song => {
                let item = [song.title, song.points]
                data.push(item);
            })
            
            console.log(data);

            this.data = data;

            //this.createChart();
        }        
    }
}
</script>