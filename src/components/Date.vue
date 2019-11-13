<template>
    <div>
        <v-spacer></v-spacer>
        <h2 class="display-1" v-bind:style="headerStyle">{{ moment().format('dddd') }}</h2>
    </div>

</template>

<script>
import moment from 'moment'

export default {
    name:"Date",
    data() {
        return {
            items: [
                1481889223,
                1452945223,
                1450871623,
                undefined,
                1450353223,
                1450270423
            ],
            headerStyle: [
                {
                    textTransform: 'capitalize',
                    padding: '10px 0',
                    fontWeight: 'thin',
                    color:'#f15e53'
                }
            ]
        }
    },
    methods: {
        moment: function (date) {
            return moment(date);
        }
    }
}
</script>

<style lang="scss" scoped>
</style>