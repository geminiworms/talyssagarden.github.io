---
layout: page
title: Home
id: home
permalink: /
---
<html>
<head>
<style>
* {
  box-sizing: border-box;
}

.column {
  float: left;
  width: 33.33%;
  padding: 5px;
}

/* Clearfix (clear floats) */
.row::after {
  content: "";
  clear: both;
  display: table;
}
</style>
</head>
<body>

  <h1>this is talyssa's [[what-is-digital-gardening|digital garden]]</h1>

<div class="row">
  <div class="column">
    <img src="assets/index/index1.png" style="height:200px">
  </div>
  <div class="column">
    <img src="assets/index/index2.png" style="height:200px">
  </div>
  <div class="column">
    <img src="assets/index/index3.png" style="height:200px">
  </div>
</div>

{% include notes_graph.html %}


<style>
  .wrapper {
    max-width: 46em;
  }
</style>
