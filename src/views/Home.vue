<template>
  <div class="jumbotron">
    <b-jumbotron class="jumbotron">
      <h1>
        Sentiment Analysis Dashboard
      </h1>
      <h4>
        Sentiment Analysis of The Effect of Vaccines on The Jabodetabek Community
      </h4>
      <div class="mx-auto" style="height: 150px;">
      </div>
      <b-button variant="primary" to="dashboard/vaksin">GO TO DASHBOARD</b-button>
    </b-jumbotron>
  </div>
</template>
<style>
.jumbotron {
    background-color: #F6FCFF !important;
    height: 200%;
    text-align: left;
    height: 100vh;
    background-image: url("../assets/jumbotron_bg.png");
    background-position: right center;
    background-repeat: no-repeat;
    background-size: 35%;
}
</style>
<script>
export default {
  name: 'Home',
}
</script>
