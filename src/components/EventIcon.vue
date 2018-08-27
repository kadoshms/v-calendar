<template>
  <svg
    class='event-icon'
    :style="style"
    :width="width"
    :height="height"
    :viewBox='viewBox'
    @click='$emit("click", $event)'>
    <g>
      <path v-for="path in paths" :d='path'>
      </path>
    </g>
  </svg>
</template>

<script>
  const _defSize = '44px';
  const _defViewBox = '0 0 32 32';
  const _defStyle = {
    fill: 'none',
  };

  const icons = {
    circle: {
      viewBox: '0 0 26 26',
      width: 38,
      height: 38,
      paths:
        ['m25.265103,12.999726c0,6.774085 -5.491018,12.265103 -12.265103,12.265103c-6.773536,0 -12.265103,-5.491018 -12.265103,-12.265103c0,-6.773536 5.491567,-12.264554 12.265103,-12.264554c6.774085,0 12.265103,5.491018 12.265103,12.264554z'],
    },
    octagon: {
      viewBox: '0 0 53 47',
      width: 38,
      height: 38,
      paths:
        ['M51.038 25.646L40.536 43.835a4.302 4.302 0 0 1-3.727 2.152H15.806a4.304 4.304 0 0 1-3.728-2.152L1.577 25.646a4.303 4.303 0 0 1 0-4.304l10.5-18.19A4.306 4.306 0 0 1 15.807 1h21.003c1.538 0 2.958.821 3.727 2.152l10.502 18.19a4.303 4.303 0 0 1 0 4.304z'],
    },
    star: {
      viewBox: '0 0 28 26',
      width: 38,
      height: 38,
      paths:
        ['m14.718297,0.810991l3.856,5.837c0.172,0.26 0.433,0.45 0.734,0.534l6.743,1.863a1.293,1.293 0 0 1 0.667,2.052l-4.36,5.47a1.293,1.293 0 0 0 -0.281,0.864l0.312,6.987a1.293,1.293 0 0 1 -1.746,1.269l-6.55,-2.456a1.29,1.29 0 0 0 -0.907,0l-6.55,2.456a1.292,1.292 0 0 1 -1.745,-1.27l0.31,-6.986a1.292,1.292 0 0 0 -0.28,-0.864l-4.36,-5.47a1.293,1.293 0 0 1 0.668,-2.052l6.742,-1.864c0.302,-0.083 0.562,-0.273 0.735,-0.534l3.855,-5.836a1.293,1.293 0 0 1 2.158,0'],
    },
    bubble: {
      viewBox: '0 0 27 26',
      width: 33,
      height: 50,
      paths:
        [
          'm10.4603,30.09065l0,1.146l3.487,-1.064l0,-1.146l-3.487,1.064zm-1,2.497l0,-3.237l5.487,-1.675l0,3.237l-5.487,1.675z',
          'm10.348,26.29035l0,-3.378l11.141,0l-11.141,3.378zm-7.623,-4.327l20.55,0l0,-20.551l-20.55,0l0,20.551zm-1,-21.551l0,22.5l7.623,0l0,4.066l0.655,0.476l14.272,-4.542l0,-22.5l-22.55,0z',
        ],
    },
    roundRect: {
      viewBox: '0 0 27 26',
      width: 33,
      height: 50,
      paths:
        [
          'm4.0685,3.326541c-0.741,0 -1.344,0.603 -1.344,1.344l0,17.863c0,0.741 0.603,1.344 1.344,1.344l17.862,0c0.742,0 1.345,-0.603 1.345,-1.344l0,-17.863c0,-0.741 -0.603,-1.344 -1.345,-1.344l-17.862,0zm17.862,21.551l-17.862,0c-1.292,0 -2.344,-1.052 -2.344,-2.344l0,-17.863c0,-1.292 1.052,-2.344 2.344,-2.344l17.862,0c1.293,0 2.345,1.052 2.345,2.344l0,17.863c0,1.292 -1.052,2.344 -2.345,2.344z',
        ],
    },
  };

  export default {
    props: ['name', 'color'],
    data() {
      return {
        width: _defSize,
        height: _defSize,
        viewBox: _defViewBox,
        style: _defStyle,
        paths: '',
        isBaseline: false,
      };
    },
    mounted() {
      this.updateIcon();
    },
    watch: {
      name() {
        this.updateIcon();
      },
    },
    methods: {
      updateIcon() {
        const icon = icons[this.name];
        if (icon) {
          this.width = icon.width || _defSize;
          this.height = icon.height || _defSize;
          this.viewBox = icon.viewBox || _defViewBox;
          this.style = icon.style || _defStyle;
          this.paths = icon.paths;
        }
      },
    },
  };
</script>

<style lang='scss' scoped>
  .event-icon {
    display: inline-block;
    stroke: currentColor;
    stroke-width: 1;
  }
</style>
