<template>
    <p :title="event.title" class="event-item" :class="cssClasses"
       @click="$emit('click', event, $event)">
        <slot :event="event" v-if="showTitle">
            Def: {{ event.title }}
        </slot>
    </p>
</template>

<script>
    import moment from 'moment'

    export default {
        props: ['event', 'date', 'firstDay','tpl'],
        computed: {
            cssClasses () {
                let cssClasses = this.event.cssClass;

                if (!Array.isArray(cssClasses)) {
                    cssClasses = [cssClasses];
                } else {
                    cssClasses = Array.from(cssClasses);
                }

                if (this.start.isSame(this.date, 'day')) {
                    cssClasses.push('is-start');
                }

                if (this.end.isSame(this.date, 'day')) {
                    cssClasses.push('is-end');
                }

                if (! this.event.isShow) {
                    cssClasses.push('is-opacity');
                }
                if(this.tpl==0){
                    cssClasses.push('event-itemFloat');
                }

                return cssClasses.join(' ');
            },
            showTitle() {
                return (this.date.day() == this.firstDay || this.start.isSame(this.date, 'day'));
            },
            start () {
                return moment(this.event.start);
            },
            end () {
                return moment(this.event.end);
            }
        }
    }
</script>