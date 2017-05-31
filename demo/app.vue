<template>
  <div>
  	<p>
  		Here is the demo of vue-fullcalendar, no jquery fullcalendar.js required!
  	</p>
    <full-calendar class="test-fc" :tpl="tpl" :itemLimit="itemLimit" :events="fcEvents"
      first-day='1' locale="zh-cn"
      @changeMonth="changeMonth"
      @eventClick="eventClick"
      @dayClick="dayClick"
      @moreClick="moreClick"
      @goPrev="goPrev"
      @goNext="goNext">
        <template slot="fc-header-left" scope="p">
            {{monthTitle}}
        </template>
        <template slot="fc-header-center" scope="p">
            周-历
        </template>
        <template slot="fc-header-right" scope="p">
            <div style="float: right">
                <span class="prev-month" @click="goPrev"><button>上一月</button></span>
                <span class="next-month" @click="goNext"><button>下一月</button></span>
            </div>
        </template>
        <template slot="fc-event-card" scope="p">
            <p>{{ p.event.title }}</p>
        </template>
    </full-calendar>
  </div>
</template>
<script>
let demoEvents = [
    {
      title    : '上8:内科',
      start    : '2017-05-3',
      end      : '2017-05-3',
      cssClass : 'family'
    },
    {
        title    : '晚9:内科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },
    {
        title    : '下8:内科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },
    {
        title    : '下7:血液',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },
    {
        title    : '下6:外科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },{
        title    : '下5:内科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },
    {
        title    : '上4:内科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },{
        title    : '上3:内科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },{
        title    : '上2:内科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    },{
        title    : '上1:内科',
        start    : '2017-05-31',
        end      : '2017-05-31',
        cssClass : 'family'
    }
  ];

export default {
	data () {
		return {
            name:'Sunny!',
            fcEvents : demoEvents,
            tpl:0,
            itemLimit:9,
            monthTitle:""
        }
	},
  methods : {

      goPrev(){
          this.$children[0].goPrev();
      },
      goNext(){
          this.$children[0].goNext();
      },
    'changeMonth' (start, end, current,foramatData) {
        this.monthTitle = foramatData(current,'MMMM YYYY');
    },


      /**
       * 日期格式化内容被点击时触发
       * @param event      {}  当前被点击内容对象
       * @param jsEvent    {}  被点击的鼠标事件对象
       * @param pos        {}  当前位置对象
       */
    'eventClick' (event, jsEvent, pos) {
       console.log('eventClick', event, jsEvent, pos)
    },
      /**
       *
       * @param day
       * @param jsEvent
       */

    'dayClick' (day, jsEvent) {
      console.log('dayClick', day, jsEvent)
    },
      /**
       *
       * @param day
       * @param events
       * @param jsEvent
       */
    'moreClick' (day, events, jsEvent) {
      //console.log('moreCLick', day, events, jsEvent)
    }
  },
  components : {
    'full-calendar' : require('src/fullCalendar')
  }
}
</script>
<style lang='scss'>
  .app{
    color:green;
  }
</style>