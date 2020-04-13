<template>
  <div id="app">
    <!-- <Complaint /> -->
    <div class="container-fluid">
      <div class="row">
        <div class="col-sm-12 col-md-6 col-lg-3">
          <h3>Identity</h3>
          <hr />
          <Identity />
        </div>
      </div>
      <div class="row"></div>
    </div>
  </div>
</template>

<script>
// import Complaint from "./components/Complaint";
import Identity from "./components/Identity";

export default {
  components: {
    // Complaint,
    Identity
  }
};
</script>

<style></style>
