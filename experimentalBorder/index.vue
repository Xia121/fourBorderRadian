<template>
<div :class="[$style[`${clsName}`]]" :style="customStyle">
    <div :class="$style[`${clsName}-${arcSrc[0]}`]" :style="borderColor"></div>
    <div :class="$style[`${clsName}-${arcSrc[1]}`]" :style="borderColor"></div>
    <div :class="$style[`${clsName}-${arcSrc[2]}`]" :style="borderColor"></div>
    <div :class="$style[`${clsName}-${arcSrc[3]}`]" :style="borderColor"></div>
    <div :class="[$style[`${clsName}-small`]]" :style="smallcustomStyle">
        <slot></slot>
    </div>
</div>
</template>

<script>
import clsMixin from '@/business-component/mixins/clsMixin.js';

export default {
    props: {
        arc: {
            type: String,
            default: '0px'
        },
        arcSrc: {
            type: Array,
            default: () => []
        },
        colors: {
            type: Array,
            default: () => ['#2d6c90','#153a4f']
        }
        /**
         * topLeft
         * topRight
         * bottomLeft
         * bottomRight
         */
    },
    data () {
        return {
            itemClsName: "smallborder",
        }
    },
    mixins: [clsMixin],
    mounted () {

    },
    computed: {
        customStyle(){
            let {arc,colors,bgswitch} = this;
            if (colors[2]) {
                //"background: rgba(28, 37, 126, 0.2)"
                return {
                    borderRadius: arc,
                    borderColor: colors[1],
                    background: colors[2]
                }
            }

            return {
                borderRadius: arc,
                borderColor: colors[1],
            }

        },
        smallcustomStyle () {
            let {arc,colors} = this;
            let background = `linear-gradient(to left , ${colors[0]}, ${colors[0]}) left top no-repeat,
            linear-gradient(to bottom, ${colors[0]}, ${colors[0]}) left top no-repeat,
            linear-gradient(to left, ${colors[0]}, ${colors[0]}) right top no-repeat,
            linear-gradient(to bottom, ${colors[0]}, ${colors[0]}) right top no-repeat,
            linear-gradient(to left, ${colors[0]}, ${colors[0]}) left bottom no-repeat,
            linear-gradient(to bottom, ${colors[0]}, ${colors[0]}) left bottom no-repeat,
            linear-gradient(to left, ${colors[0]}, ${colors[0]}) right bottom no-repeat,
            linear-gradient(to left, ${colors[0]}, ${colors[0]}) right bottom no-repeat`

            return {
                borderRadius: arc,
                background: background,
                backgroundSize: '1px 20px, 20px 1px, 1px 20px, 20px 1px'
            }
        },
        borderColor () {
            let {colors} = this;

            return {
                borderColor: colors[0]
            }
        }
    },
}
</script>
<style module lang="less">
@import "./index.less";
</style>