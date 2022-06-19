<template>
<div class="total">
  <nav class="navbar navbar-expand-sm navbar-dark bg-dark">
      <a class="navbar-brand ms-auto me-auto" href="#">Vue.Chart.Js</a>
      <button class="navbar-toggler d-lg-none" type="button" data-bs-toggle="collapse" data-bs-target="#collapsibleNavId" aria-controls="collapsibleNavId"
          aria-expanded="false" aria-label="Toggle navigation"></button>
      <!-- <div class="collapse navbar-collapse" id="collapsibleNavId">
          <ul class="navbar-nav me-auto mt-2 mt-lg-0">
              <li class="nav-item active">
                  <a class="nav-link" href="#">Home <span class="visually-hidden">(current)</span></a>
              </li>
              <li class="nav-item">
                  <a class="nav-link" href="#">Link</a>
              </li>
              <li class="nav-item dropdown">
                  <a class="nav-link dropdown-toggle" href="#" id="dropdownId" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">Dropdown</a>
                  <div class="dropdown-menu" aria-labelledby="dropdownId">
                      <a class="dropdown-item" href="#">Action 1</a>
                      <a class="dropdown-item" href="#">Action 2</a>
                  </div>
              </li>
          </ul>
      </div> -->
  </nav>
  <div id="app" class="container">
    <div class="btn-group mt-3" role="group" aria-label="Basic radio toggle button group">
      <input type="radio" class="btn-check" name="btnradio" id="btnradio1" autocomplete="off" checked>
      <label @click="LineStep()" class="btn btn-outline-success" for="btnradio1">LINE</label>

      <input type="radio" class="btn-check" name="btnradio" id="btnradio2" autocomplete="off">
      <label @click="BarStep()" class="btn btn-outline-success" for="btnradio2">BAR</label>

      <input type="radio" class="btn-check" name="btnradio" id="btnradio3" autocomplete="off">
      <label @click="DoughnutStep()" class="btn btn-outline-success" for="btnradio3">DOUGHNUT</label>

      <input type="radio" class="btn-check" name="btnradio" id="btnradio4" autocomplete="off">
      <label @click="PieStep()" class="btn btn-outline-success" for="btnradio4">PIE</label>

    </div>
    <div class="row col-10 col-md-10 col-sm-12 ms-auto me-auto">
      <component :is="currentTab"></component>
      <!-- <LineChart/>
      <BarChart/>
      <DoughnutChart/>
      <PieChart/> -->
    </div>
  </div>
</div>
</template>

<script>
import LineChart from "./components/LineChart";
import BarChart from "./components/BarChart";
import DoughnutChart from "./components/DoughnutChart";
import PieChart from "./components/PieChart";

export default {
  name: "App",
  components: {
    LineChart,
    BarChart,
    DoughnutChart,
    PieChart,
  },
  data() {
    return {
      tabs: ["LineChart", "BarChart", "DoughnutChart", "PieChart"],
      currentTab: "LineChart",
    };
  },
  methods: {
    LineStep() {
      this.currentTab = "LineChart";
    },
    BarStep() {
      this.currentTab = "BarChart";
    },
    DoughnutStep() {
      this.currentTab = "DoughnutChart";
    },
    PieStep() {
      this.currentTab = "PieChart";
    },
  },
};
</script>
<style scoped>
  .total{
    position: fixed;
    top:0;
    bottom:0;
    right:0;
    left:0;
    background-color:rgb(213, 217, 216);
  }
  button{
    display: inline-block;
  }
</style>