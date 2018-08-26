<template>
  <svg
    class='event-icon'
    :style="style"
    :width='width'
    :height='height'
    :viewBox='viewBox'
    @click='$emit("click", $event)'>
    <path :d='path'>
    </path>
  </svg>
</template>

<script>
  const _defSize = '26px';
  const _defViewBox = '0 0 32 32';
  const _defStyle = {
    fill: 'none',
  };

  const icons = {
    circle: {
      viewBox: '0 0 32 32',
      path:
        'M13.219 1.01c-6.341 0-11.5 5.16-11.5 11.5 0 6.342 5.159 11.5 11.5 11.5 6.34 0 11.5-5.158 11.5-11.5 0-6.34-5.16-11.5-11.5-11.5m0 24c-6.893 0-12.5-5.606-12.5-12.5 0-6.892 5.607-12.5 12.5-12.5s12.5 5.608 12.5 12.5c0 6.894-5.607 12.5-12.5 12.5',
    },
    octagon: {
      viewBox: '0 0 53 47',
      path:
        'M51.038 25.646L40.536 43.835a4.302 4.302 0 0 1-3.727 2.152H15.806a4.304 4.304 0 0 1-3.728-2.152L1.577 25.646a4.303 4.303 0 0 1 0-4.304l10.5-18.19A4.306 4.306 0 0 1 15.807 1h21.003c1.538 0 2.958.821 3.727 2.152l10.502 18.19a4.303 4.303 0 0 1 0 4.304z',
    },
    star: {
      viewBox: '0 0 27 26',
      path:
        'M14.57.58l3.856 5.837c.172.26.433.45.734.534l6.743 1.863a1.293 1.293 0 0 1 .667 2.052l-4.36 5.47a1.293 1.293 0 0 0-.281.864l.312 6.987a1.293 1.293 0 0 1-1.746 1.269L13.945 23a1.29 1.29 0 0 0-.907 0l-6.55 2.456a1.292 1.292 0 0 1-1.745-1.27l.31-6.986a1.292 1.292 0 0 0-.28-.864l-4.36-5.47a1.293 1.293 0 0 1 .668-2.052L7.823 6.95c.302-.083.562-.273.735-.534L12.413.58a1.293 1.293 0 0 1 2.158 0',
    },
  };

  export default {
    props: ['name'],
    data() {
      return {
        width: _defSize,
        height: _defSize,
        viewBox: _defViewBox,
        style: _defStyle,
        path: '',
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
          this.path = icon.path;
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
