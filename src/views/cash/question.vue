<template>
  <div style="overflow: auto;height: 500px;">
    <span style="font-size: 24px"><b>&nbsp;电信收费问题</b></span>
    <div style="font-size: 16px">
      <p>研究与我们的生活息息相关的电信收费问题系统，需求描述如下：</p>
      <p>
        A.
        <b>每月的电话总费用=基本月租费+折扣后的实际的通话费</b
        >，如果没有折扣则按实际通话费计算，基本月租费为25元，每分钟通话费为0.15元。
      </p>
      <p>
        B.
        实际通话费是否有折扣与当月的通话时间（分钟）和本年度至本月的累计未按时缴费的次数有关。
      </p>
      <p>
        C.
        当月的通话分钟数和折扣比例及本年度未按时缴费次数之间有直接的对应关系，如果本年度的未按时缴费的次数超过本月通话时间所对应的容许值则免于折扣，并按实际的通话费计算。
      </p>
      <p>D. 通话时间和折扣比例及未按时缴费次数的关系为：</p>
      <el-table :data="questionData" style="width: 100%; font-size: 16px">
        <el-table-column
          prop="minute"
          label="本月通话的分钟数"
          width="400"

          align="center"
        >
        </el-table-column>
        <el-table-column
          prop="times"
          label="通话时间段的最大容许不按时缴费次数"
          width="400"
          align="center"
        >
        </el-table-column>
        <el-table-column
          prop="discount"
          label="通话时间段的折扣率"
          align="center"
        >
        </el-table-column>
      </el-table>

      <p>
        在设计测试用例前，我们首先对问题进行分析，得到变量的边界值，易知：
        0 &lt= T &lt= 44640    分钟
        本年度未按时缴费次数范围为： 0 &lt= C  &lt= 11 次
      </p>

      <span style="font-size: 24px"><b>边界值法</b></span>

      <p> 这里我们选用健壮性边界测试法：由T、C的取值范围，我们取T的平均值为： 22320分钟；C的平均值为：6次</p>
      <img src="./边界值.png" style="width:100%;height:100%;object-fit: fill;" />

      <span style="font-size: 24px"><b>等价类法</b></span>
      <p> 对于变量T，我们可以根据定价规则划分出5个有效等价区间，以及两个无效等价区间，他们分别是：</p>
      <p>0 &lt= T&lt= 60、60 &lt T &lt= 120、120 &lt T &lt= 180、180 &lt T &lt= 300、300 &lt T &lt= 44640</p>
      <p>T &lt 0、T > 44640</p>
      <p>对于变量C，我们也可以划分出5个有效等价区间，以及两个无效等价区间，他们分别是：</p>
      <p>0 &lt= C &lt= 1、 1 &lt C &lt= 2、 2 &lt C &lt= 3、 3 &lt C &lt= 6、 6 &lt C &lt= 11</p>
      <p>C &lt 0、C > 11</p>
      <p>根据上述区间，我们使用强健壮类方法设计我们的测试用例，为：</p>
      <img src="./健壮等价类1.png" style="width:100%;height:100%;object-fit: fill;" />
      <img src="./健壮等价类2.png" style="width:100%;height:100%;object-fit: fill;" />
      <img src="./健壮等价类3.png" style="width:100%;height:100%;object-fit: fill;" />

      <span style="font-size: 24px"><b>决策表法</b></span>
      <p>根据题意，我们绘制出的决策表为</p>
      <img src="./决策表.png" style="width:100%;height:100%;object-fit: fill;" />
      <p>对应的测试用例为</p>
      <img src="./决策表测试用例.png" style="width:100%;height:100%;object-fit: fill;" />
    </div>
  </div>
</template>

<script>
export default {
  name: "CashQuestion",
  components: {},
  props: {},
  data() {
    return {
      questionData: [
        {
          minute: "0<通话时间≤60",
          times: 1,
          discount: "1.0%",
        },
        {
          minute: "60<通话时间≤120",
          times: 2,
          discount: "1.5%",
        },
        {
          minute: "120<通话时间≤180",
          times: 3,
          discount: "2.0%",
        },
        {
          minute: "180<通话时间≤300",
          times: 3,
          discount: "2.5%",
        },
        {
          minute: "通话时间>300",
          times: 6,
          discount: "3.0%",
        },
      ],
    };
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {},
  methods: {},
};
</script>

<style scoped lang="less">
</style>