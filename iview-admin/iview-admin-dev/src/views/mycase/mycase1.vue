<template>
    <Transfer
        :data="data1"
        :target-keys="targetKeys1"
        :render-format="render1"
        @on-change="handleChange1"></Transfer>
</template>
<script>
    export default {
        data () {
            return {
                data1: this.getMockData(),
                targetKeys1: this.getTargetKeys()
            }
        },
        methods: {
            getMockData () {
                let mockData = [];
                for (let i = 1; i <= 20; i++) {
                    mockData.push({
                        key: i.toString(),
                        label: 'Content ' + i,
                        description: 'The desc of content  ' + i,
                        disabled: Math.random() * 3 < 1
                    });
                }
                return mockData;
            },
            getTargetKeys () {
                return this.getMockData()
                        .filter(() => Math.random() * 2 > 1)
                        .map(item => item.key);
            },
            render1 (item) {
                return item.label;
            },
            handleChange1 (newTargetKeys, direction, moveKeys) {
                console.log(newTargetKeys);
                console.log(direction);
                console.log(moveKeys);
                this.targetKeys1 = newTargetKeys;
            }
        }
    }
</script>
<style>
	.main .single-page-con {
	    position: absolute;
	    top: 100px;
	    right: 0;
	    bottom: 0;
	    overflow: auto;
	    background-color: #ffffff;
	    z-index: 1;
	    transition: left .3s;
	}
</style>