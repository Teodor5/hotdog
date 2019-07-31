<template>
  <div>

    <div>
            <h1>Hello, are you hungry?</h1>
      <div class="video-container"><iframe width="560" height="315" src="https://www.youtube.com/embed/ykTR0uFGwE0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>
      <h3><router-link v-bind:to="{ name: 'Posts' }" class="add_post_link">View Hot Dog App</router-link></h3>
    </div>
    <div class="flex-container">
      <div class="unit">
        <div class="hotdog-unit">
          <div class="bread left"></div>
          <div class="hotdog">
            <div class="mustard"></div>
          </div>
          <div class="bread right"></div>
        </div>
        <div class="shadow"></div>
      </div>
    </div>
</div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

  @import '../../src/assets/css/hotdog.css';

h1, h2 {
  font-weight: bold;
  color: #37BBD4;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #EE5D1E;
}

@media only screen and (max-width:768px) {
  .video-container {
    position: relative;
    padding-bottom: 56.25%;
    padding-top: 30px; height: 0; overflow: hidden;
  }

  .video-container iframe,
  .video-container object,
  .video-container embed {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}

</style>
