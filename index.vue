<template>
    <div :class="$style[`${clsName}`]">
        <experimentalBorder  :class="$style[`${clsName}-passenger`]" :arc="arc" :arcSrc="arcSrc">
            <PassengerFlow></PassengerFlow>
        </experimentalBorder>
        <experimentalBorder  :class="$style[`${clsName}-flowCity`]" :arc="arcR" :arcSrc="arcSrcR">
            <Distance></Distance>
        </experimentalBorder>
    </div>
</template>

<script>
import clsMixin from '@/business-component/mixins/clsMixin.js';
import PassengerFlow from './passengerFlow.vue';
import Distance from './distance.vue';
import experimentalBorder from '@/business-component/experimentalBorder';

export default {
    data () {
        return {
            itemClsName: 'population-top',
            margin: '0 0 0 0',
            arc: '20px 0 0 0',
            arcSrc: ['topLeft'],
            arcR: '0 20px 0 0',
            arcSrcR: ['topRight']
        }
    },
    mixins: [clsMixin],
    components: {
        PassengerFlow,
        Distance,
        experimentalBorder
    }
}
</script>
<style module lang="less">
@import "./index.less";
</style>