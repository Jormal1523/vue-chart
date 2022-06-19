<script>
import axios from "axios";
import { defineComponent, onMounted, ref, h, PropType } from "vue";
import { Line } from "vue-chartjs";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  LineElement,
  LinearScale,
  PointElement,
  CategoryScale,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  LineElement,
  LinearScale,
  PointElement,
  CategoryScale
);

export default defineComponent({
  name: "LineChart",
  components: {
    Line,
  },
  // data(){
  //   return{
  //     dateArr:[]
  //   }
  // },
  props: {
    chartId: {
      type: String,
      default: "line-chart",
    },
    width: {
      type: Number,
      default: 400,
    },
    height: {
      type: Number,
      default: 400,
    },
    cssClasses: {
      default: "",
      type: String,
    },
  },
  // async mounted(){
  //   let { data } = await axios.get('https://api.covidtracking.com/v1/us/daily.json')
  //   // console.log(data)
  //   for(let value of data){
  //     this.dateArr.push(value.date)
  //   }
  //   console.log(this.dateArr)
  // },
  setup(props) {
    const dateArr = ref([]);
    onMounted(async () => {
      const res = await axios.get("https://api.covidtracking.com/v1/us/daily.json");
      dateArr.value = res.data;
      console.log(dateArr.value);
      for (let i = 0; i < dateArr.value.length; i++) {
      console.log(dateArr.value[i].date);
      }   
    });
    
    const chartData = {
      labels: dateArr.date,
      datasets: [
        {
          label: "Data One",
          backgroundColor: "#f87979",
          data: dateArr.death,
        },
      ],
    };

    const chartOptions = {
      responsive: true,
      maintainAspectRatio: false,
    };
    return () =>
      h(Line, {
        chartData,
        chartOptions,
        chartId: props.chartId,
        width: props.width,
        height: props.height,
        cssClasses: props.cssClasses,
      });
  },
});
</script>
