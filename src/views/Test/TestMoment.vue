<template>
    <div>
        <div>양력: {{ getHumanDate('19720126') }}</div>
        <div>음력: {{ getHumanDateLunar('19720126') }}</div>
        <div>{{ $moment('19720126', 'YYYYMMDD').lunar() }}</div>
    </div>
</template>

<script>
//import moment from 'moment';

export default {
    data: function() {
        return {};
    },
    beforeMount: function() {
        this.test();
    },
    methods: {
        getHumanDate: function(date) {
            return this.$moment(date, 'YYYYMMDD').format('YYYY-MM-DD');
            //return moment(date, 'YYYYMMDD').format('DD/MM/YYYY');
            //return date;
        },
        getHumanDateLunar: function(date) {
            return this.$moment(date, 'YYYYMMDD')
                .lunar()
                .format('YYYY-MM-DD');
            //return moment(date, 'YYYYMMDD').format('DD/MM/YYYY');
            //return date;
        },
        test() {
            var date = this.$moment('20170101', 'YYYYMMDD').lunar();
            var date7 = this.$moment('20170108', 'YYYYMMDD').lunar();
            var mins7 = this.$moment('20170101 00:07', 'YYYYMMDD HH:mm').lunar();
            var secs1 = this.$moment('20170101 00:00:01', 'YYYYMMDD HH:mm:ss').lunar();

            console.log(date7.diff(date, 'days') + 'd'); // "7d"
            console.log(mins7.diff(date, 'minutes') + 'm'); // "7m"
            console.log(secs1.diff(date, 'seconds') + 's'); // "1s"
        }
    }
};
</script>
