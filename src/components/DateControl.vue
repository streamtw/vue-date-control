<template lang="pug">
  .date-control
</template>

<script>
import moment from 'moment'

export default {
  name: 'DateControl',
  props: {
    msg: String,
    value: Object,
  },
  data () {
    return {
      date: moment(),
    }
  },
  mounted () {
    moment.locale('zh-TW')
    this.$_fireEvent()
  },
  methods: {
    add (type) {
      this.date.add(1, type)
      this.$_fireEvent()
    },
    subtract (type) {
      this.date.subtract(1, type)
      this.$_fireEvent()
    },
    $_getWeekdayLabel (weekdayIndex) {
      return moment.weekdaysMin()[weekdayIndex]
    },
    $_fireEvent () {
      this.$emit('input', {
        year: this.date.year(),
        month: this.date.month() + 1,
        day: this.date.date(),
        weekday: this.$_getWeekdayLabel(this.date.weekday()),
      })
    },
  },
}
</script>

<style lang="sass">
//
</style>
