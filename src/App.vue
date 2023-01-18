<script>
  export default {
    data() {
      return {
        items: Array.from({ length: 9 }, (_, i) => i),
        flashIndex: [2, 4, 8],
        circleIndex: [0, 2, 6, 8]
        // another way to setting
        // firstCircleTransform: "translate(-50%, -50%)",
        // secCircleTransform: "translate(-50%, -50%)",
        // thirdCircleTransform: "translate(-50%, -50%)",
        // fourCircleTransform: "translate(-50%, -50%)"
      };
    },
    mounted() {
      this.flash();
      // then after 5200ms will be static
      // setTimeout(() => {
      //   this.firstCircleTransform = "translate(490px, 235px)";
      //   this.secCircleTransform = "translate(80px, 235px)";
      //   this.thirdCircleTransform = "translate(490px, 25px)";
      //   this.fourCircleTransform = "translate(80px, 25px)";
      //   // this.$refs.firstCircle.style.transform = "translate(150%, 150%)";
      // }, 5200);
    },
    methods: {
      flash() {
        setInterval(() => {
          this.flashIndex.forEach((index) => {
            const grid = this.$el.getElementsByClassName("grid-item")[index];
            grid.style.opacity = grid.style.opacity === "1" ? "0.6" : "1";
          });
        }, 500);
      }
    }
  };
</script>

<template>
    <div id="app">
      <div
        v-for="(item, index) in items"
        :key="index"
        :class="{
          flash: flashIndex.includes(index),
          circle: circleIndex.includes(index)
        }"
        class="grid-item"
       >
        <div
          v-if="index === 0"
          ref="firstCircle"
          v-bind:style="{ transform: firstCircleTransform }"
          class="firstCircle"
        ></div>
        <div
          v-if="index === 2"
          ref="secCircle"
          v-bind:style="{ transform: secCircleTransform }"
          class="secCircle"
        ></div>
        <div
          v-if="index === 6"
          ref="thirdCircle"
          v-bind:style="{ transform: thirdCircleTransform }"
          class="thirdCircle"
        ></div>
        <div
          v-if="index === 8"
          ref="fourthCircle"
          v-bind:style="{ transform: fourCircleTransform }"
          class="fourthCircle"
        ></div>
      </div>
    </div>  
</template>