<template>
  <div class="header">
    <a href="#default" class="logo"> <img src="logo.png" alt="" /></a>
    <div class="header-right">
      <a class="active" href="#home">Home</a>
      <a href="#manage">Admin</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyHeader",
};
</script>

<style scoped>
img {
  width: 75px;
}
.header {
  overflow: hidden;
  padding: 20px 10px;
}

.header a {
  float: left;
  color: black;
  text-align: center;
  padding: 12px;
  text-decoration: none;
  font-size: 18px;
  line-height: 25px;
  border-radius: 4px;
}

.header a.logo {
  font-size: 25px;
  font-weight: bold;
}

.header a:hover {
  background-color: #ddd;
  color: black;
}

.header a.active {
  background-color: dodgerblue;
  color: white;
}

.header-right {
  float: right;
}

@media screen and (max-width: 500px) {
  .header a {
    float: none;
    display: block;
    text-align: left;
  }
  .header-right {
    float: none;
  }
}
</style>
