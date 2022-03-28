---
layout: page
title: Home
id: home
permalink: /
---

# this is talyssa's [[what-is-digital-gardening|digital garden]] 

<div class="row">
  <div class="column">
    <img src="assets/index/index1.png" style="height:50%">
  </div>
  <div class="column">
    <img src="assets/index/index2.png" style="height:50%">
  </div>
  <div class="column">
    <img src="assets/index/index3.png" style="height:50%">
  </div>
</div>

<!-- Three image containers (use 25% for four, and 50% for two, etc) -->
.column {
  float: left;
  width: 33.33%;
  padding: 5px;
}

<!-- Clear floats after image containers -->
.row::after {
  content: "";
  clear: both;
  display: table;
}

{% include notes_graph.html %}


<style>
  .wrapper {
    max-width: 46em;
  }
</style>
