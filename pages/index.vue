<template>
  <div class="container">
    <div>
      <h1 class="title">
        How many times has your friend been a douche tonight? <span @click="reset()" style="color:red">CLEAR</span>
      </h1>
      <div class="frame">
        <div class="center">
          <div class="button" @click="increase">
            <span>{{ count }} Times</span>
            <svg width="180px" height="60px" viewBox="0 0 180 60" class="border">
              <polyline points="179,1 179,59 1,59 1,1 179,1" class="bg-line"/>
              <polyline points="179,1 179,59 1,59 1,1 179,1" class="hl-line"/>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    this.count = this.$cookies.get('count');
  },
  data() {
    return {
      count: 0
    }
  },
  methods: {
    increase() {
      let cookie = this.$cookies.get('count');
      cookie ??= 0;
      cookie++;

      this.$cookies.set('count', cookie);
      this.count = cookie;
    },
    reset() {
      this.$cookies.set('count', 0);
      this.count = 0;
    }
  }
}
</script>

<style lang="scss">
// delete the following line if no text is used
// edit the line if you wanna use other fonts
@import url(https://fonts.googleapis.com/css?family=Open+Sans:700,600,300);

// use only the available space inside the 400x400 frame
.frame {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 400px;
  height: 400px;
  margin-top: -200px;
  margin-left: -200px;
  border-radius: 2px;
  box-shadow: 4px 8px 16px 0 rgba(0, 0, 0, 0.1);
  overflow: hidden;
  background: #23074d; /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #cc5333, #23074d); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #cc5333, #23074d); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  color: #333;
  font-family: 'Open Sans', Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.button {
  position: relative;
  cursor: pointer;

  span {
    position: absolute;
    text-align: center;
    line-height: 55px;
    left: 0;
    right: 0;
    color: #42A5F5;
    text-transform: uppercase;
    font-size: 20px;
    font-weight: 600;
    letter-spacing: 1px;
    transition: all 0.3s ease-in-out;
  }

  .border {
    fill: none;
    stroke-width: 3;
  }

  .bg-line {
    fill: rgba(204, 83, 51, .4);
    stroke: #91C9FF;
    transition: all 0.6s ease-in-out;
  }

  .hl-line {
    stroke: #FF3D00;
    stroke-dasharray: 40 480;
    stroke-dashoffset: 40;
    transition: all 0.6s ease-in-out;
  }

  &:hover {
    span {
      color: #ECEFF1;
    }

    .bg-line {
      fill: #303F9F;
    }

    .hl-line {
      stroke-dashoffset: -480;
      stroke: #EEFF41;
    }
  }
}
</style>
