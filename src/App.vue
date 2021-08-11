<template lang="pug">
#app
  DateControl(ref="date" v-model="dateOfComponent" @input="show")
  .formatted-date {{ dateOfComponent.year }} 年 {{ dateOfComponent.month }} 月 {{ dateOfComponent.day }} 日 ({{ dateOfComponent.weekday }})
  .date-picker-wrapper
    .date-picker
      button.date-picker__button.date-picker__button--add(@click="$refs.date.add('year')")
      .date-picker__value {{ dateOfComponent.year }}
      button.date-picker__button.date-picker__button--subtract(@click="$refs.date.subtract('year')")
    .date-picker
      button.date-picker__button.date-picker__button--add(@click="$refs.date.add('month')")
      .date-picker__value {{ dateOfComponent.month }}
      button.date-picker__button.date-picker__button--subtract(@click="$refs.date.subtract('month')")
    .date-picker
      button.date-picker__button.date-picker__button--add(@click="$refs.date.add('day')")
      .date-picker__value {{ dateOfComponent.day }}
      button.date-picker__button.date-picker__button--subtract(@click="$refs.date.subtract('day')")
</template>

<script>
import DateControl from '@/components/DateControl'

export default {
  components: { DateControl },
  data () {
    return {
      dateOfComponent: {},
    }
  },
  methods: {
    show () {
      console.log(this.dateOfComponent)
    },
  },
}
</script>

<style lang="sass">
*
  box-sizing: border-box

#app
  width: 100vw
  height: 100vh
  padding: 100px

  .formatted-date
    text-align: center
    font-size: 1.5rem

  .date-picker-wrapper
    display: flex
    align-items: center
    justify-content: center
    margin-top: 32px

  .date-picker
    text-align: center

    > * + *
      margin-top: 8px

    .date-picker__button
      background: none
      border-right: 24px solid transparent
      border-left: 24px solid transparent
      height: 0
      padding: 0

      &.date-picker__button--add
        border-bottom: 24px solid black
        border-top: none

      &.date-picker__button--subtract
        border-top: 24px solid black
        border-bottom: none

  .date-picker + .date-picker
    margin-left: 32px

</style>
