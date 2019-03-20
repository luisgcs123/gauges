<template>
  <div class="dashboard">
    <v-layout row wrap>
      <v-flex xs10 sm10 lg10 >
          <v-toolbar color="light-blue accent-2" class="elevation-3 pa-3">
            <v-toolbar-title class="white--text headline mb-0">Everything is good! Touch anywhere to start</v-toolbar-title>
          </v-toolbar> 
      </v-flex>
      <v-flex xs2 sm2 lg2 >
        <v-icon x-large color="white" class="px-3 mx-3 ">question_answer</v-icon>
        <v-icon x-large color="white" class="px-3 mx-3">share</v-icon>
      </v-flex>
    </v-layout>
  <v-layout wrap row>
      <v-flex xs12 sm12 md6 lg6 class="justify-center text-xs-center">
        <linear-gauge :value="value" :options="options"></linear-gauge>
      </v-flex>
      <v-flex xs12 sm12 md6 lg6 class="justify-center text-xs-center">
        <ve-gauge :data="chartData" :settings="chartSettings"></ve-gauge>
      </v-flex>
  </v-layout>
  </div>
</template>
 
<script>
import VeGauge from 'v-charts/lib/gauge.common'
import LinearGauge from 'vue2-canvas-gauges/src/LinearGauge'
export default {
  components: { VeGauge, LinearGauge },
  props: {
      value: {
        type: Number,
        default: -171
      },
      options: { // https://canvas-gauges.com/documentation/user-guide/configuration
        type: Object,
        default: () => ({
          units: '°C',
          title: 'Temperature',
          minValue: -195,
          maxValue: -135,
          width: 120,
          height: 400,
          strokeTicks: true,
          colorBar: 'transparent',
          colorBarProgress: 'white',
          highlights: [ {
            'from': -195,
            'to': -155,
            'color': '#44c153'
          },
           {
            'from': -155,
            'to': -145,
            'color': '#ecda27'
          },
           {
            'from': -145,
            'to': -135,
            'color': '#ec6a49'
          }
          ],
          minorTicks: 10,
          majorTicks: [
            '-195',
            '-180',
            '-165',
            '-150',
            '-135'
          ],
          colorMajorTicks:'transparent', 
          colorMinorTicks:'transparent', 
          colorTitle: 'white',
          colorPlate: 'transparent',
          colorNumbers: 'white',
          borderShadowWidth: 0,
          borders: false,
          needleType: 'line',
          needleShadow: true,
          needleWidth: 6,
          needleCircleSize: 7,
          needleCircleOuter: true,
          needleCircleInner: true,
          colorNeedle: "white",
          numberSide: 'left',
          tickSide: 'left',
          needleSide: 'left',
          ticksWidth: 10,
          ticksPadding: 5,
          ticksWidthMinor: 10,
          colorValueText: 'white',
          colorValueTextShadow: 'transparent',
          colorValueBoxBackground: 'transparent',
          colorValueBoxShadow: 'transparent',
          borderShadowWidth: 0,
          barStrokeWidth: 0,
          colorUnits: 'white',
          barWidth: 4,
          valueBox: true,
          valueBoxStroke: 0,
          valueTextShadow: false,
          valueDec: 1,
          barBeginCircle: 4,
          fontNumbersSize: 28,
          fontUnitsSize: 30,
          fontValueSize: 30
        })
      }
  },
    data () {
    this.chartSettings = {
      seriesMap: {
          'inches': {
            min:0,
            max:12,
            splitNumber:6,
            startAngle:180,
            endAngle:0,
            detail: {
              backgroundColor: 'white',
              textStyle: {
                fontWeight: 'bolder'
              }
            },
            axisLine:{
              
              lineStyle: { 
                color: [ [ 0.167 ,'#ec6a49' ],[ 0.5,'#ecda27'],[ 1, '#44c153'] ], 
                opacity: 1,
                width:10,
              },
            },
            splitLine:{
              length:15,
              lineStyle:{
                color: 'white',
                opacity: 0.1,
              }
            },
            axisTick:{
              splitNumber: 2,
              length: 15,
              lineStyle: {
                color: 'auto',
              },
            },
            axisLabel:{
              formatter: '{value} " ',
            },
          }
      },
      dataName: {
        'speed': '"'
      }
    }
    return {
      chartData: {
        columns: ['type', 'value'],
        rows: [
          { type: 'inches', value: 10.1 }
        ]
      }
    }
  }
}
</script>
<style>
.speech-bubble {
	position: relative;
	background: #00aabb;
	border-radius: .4em;
}

.speech-bubble:after {
	content: '';
	position: absolute;
	left: 0;
	top: 50%;
	width: 0;
	height: 0;
	border: 35px solid transparent;
	border-right-color: #00aabb;
	border-left: 0;
	margin-top: -35px;
	margin-left: -35px;
}
</style>