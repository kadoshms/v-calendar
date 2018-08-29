<template>
  <div id="app">
    <v-calendar @move-clicked="foo"
                :attributes="attributes"
                :current-day-color="'red'"
                :locale="'he'"></v-calendar>
  </div>
</template>

<script>
  import Vue from 'vue';
  import VCalender from './lib';

  Vue.use(VCalender, {
    locale: 'he',
  });


  export default {
    name: 'App',
    data() {
      return {
        attributes: [{
          score: 1,
          eventIcon: {
            backgroundColor: 'red',
            type: 'roundRect',
          },
          dates: {
            start: new Date(2018, 7, 27),
            end: new Date(2018, 7, 27),
          },
        }, {
          score: 1,
          eventIcon: {
            backgroundColor: 'red',
            type: 'star',
          },
          dates: {
            start: new Date(2018, 7, 28),
            end: new Date(2018, 7, 28),
          },
        }, {
          score: 1,
          eventIcon: {
            backgroundColor: 'red',
            type: 'star',
          },
          dates: {
            start: new Date(2018, 7, 28),
            end: new Date(2018, 7, 28),
          },
        },
          {
            score: 1,
            eventIcon: {
              backgroundColor: 'red',
              type: 'star',
            },
            dates: {
              start: new Date(2018, 7, 28),
              end: new Date(2018, 7, 28),
            },
          }, {
            score: 3,
            eventIcon: {
              backgroundColor: 'red',
              type: 'circle',
            },
            dates: {
              start: new Date(2018, 7, 29),
              end: new Date(2018, 7, 29),
            },
          }, {
            score: 3,
            eventIcon: {
              backgroundColor: 'red',
              type: 'octagon',
            },
            dates: {
              start: new Date(2018, 7, 30),
              end: new Date(2018, 7, 30),
            },
          }, {
            score: 44,
            eventIcon: {
              backgroundColor: 'red',
              type: 'bubble',
            },
            dates: {
              start: new Date(2018, 8, 31),
              end: new Date(2018, 8, 31),
            },
          }, {
                score: 1004,
                eventIcon: {
                    backgroundColor: 'red',
                    type: 'bubble',
                },
                dates: {
                    start: new Date(2018, 7, 26),
                    end: new Date(2018, 7, 26),
                },
            }, {
                score: 44,
                eventIcon: {
                    backgroundColor: 'red',
                    type: 'bubble',
                },
                dates: {
                    start: new Date(2018, 8, 31),
                    end: new Date(2018, 8, 31),
                },
            }],
      };
    },
    methods: {
      foo(x) {
        console.log('next', x);
      },
    },
  };
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
