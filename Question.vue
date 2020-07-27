<template>
  <div class="container">
    <h2>骨科术后管理问卷</h2>
    <div class="index-title">
      <div class="el-input">
        姓名：
        <el-input v-model="model.name" style="width: 100px;"></el-input>年龄：
        <el-input v-model="model.age" style="width: 100px;"></el-input>
      </div>
      <div class="el-input">
        身高：
        <el-input v-model="model.height" style="width: 100px;"></el-input>当前体重：
        <el-input v-model="model.weight" style="width: 100px;"></el-input>
      </div>
    </div>
    <div class="title1-info">
      <h4>一、一般信息</h4>
      <div class="title1">
        <div style="margin-bottom: 10px;">1.您的口味与周围的人相比如何？（单选）</div>
        <el-radio v-model="model.radio" label="1">很淡</el-radio>
        <el-radio v-model="model.radio" label="2">略淡</el-radio>
        <el-radio v-model="model.radio" label="3">相同</el-radio>
        <el-radio v-model="model.radio" label="4">略咸</el-radio>
      </div>
      <div class="title2">
        <div style="margin-bottom: 10px;">2.您每顿饭吃几成饱？（单选）</div>
        <el-radio v-model="model.radio1" label="1">六成饱</el-radio>
        <el-radio v-model="model.radio1" label="2">七成饱</el-radio>
        <el-radio v-model="model.radio1" label="3">八成饱</el-radio>
        <el-radio v-model="model.radio1" label="4">九成饱</el-radio>
        <el-radio v-model="model.radio1" label="4">过饱</el-radio>
      </div>
      <div class="title3">
        <div style="margin-bottom: 10px;">3.您三餐的饮食分配比例？（按十份算）</div>早餐：
        <el-input type="number" v-model="model.radio2_1" style="width:60px"></el-input>午餐：
        <el-input type="number" v-model="model.radio2_2" style="width:60px"></el-input>晚餐：
        <el-input type="number" v-model="model.radio2_3" style="width:60px"></el-input>
      </div>
      <div class="title4">
        <div style="margin-bottom: 10px;">4.您饮食品种是否多样化？（每天多于12种，每周多于25种算多样）</div>
        <el-radio v-model="model.radio3" label="1">是</el-radio>
        <el-radio v-model="model.radio3" label="2">否</el-radio>
      </div>
      <div class="title5">
        <div style="margin-bottom: 10px;">5.您每天大约饮水量（ ）ml。</div>
        <el-radio v-model="model.radio4" label="1">小于1000</el-radio>
        <el-radio v-model="model.radio4" label="2">1000-1500</el-radio>
        <el-radio v-model="model.radio4" label="3">1500-2000</el-radio>
        <el-radio v-model="model.radio4" label="4">大于2000</el-radio>
      </div>
      <div class="title6">
        <div style="margin-bottom: 10px;">6.您目前食欲如何</div>
        <el-radio v-model="model.radio5" label="1">良好</el-radio>
        <el-radio v-model="model.radio5" label="2">欠佳</el-radio>
      </div>
      <div class="title7">
        <div style="margin-bottom: 10px;">7.是否服用膳食补充剂</div>
        <el-radio v-model="model.radio6" label="1" @change="changeLabel">是</el-radio>
        <div :class="isShow? 'yes_click':'yes' ">
          有哪些：
          <el-input v-model="model.radio6_1" style="width: 100px"></el-input>
        </div>
        <el-radio v-model="model.radio6" label="2" @change="changeNoLabel">否</el-radio>
      </div>
      <div class="title8">
        <div style="margin-bottom: 10px;">8.大便情况</div>
        <el-radio v-model="model.radio7" label="1">正常</el-radio>
        <el-radio v-model="model.radio7" label="2">便秘</el-radio>
      </div>
    </div>
    <div class="title2-info">
      <h4>二、化验检查结果（填数值）</h4>
      <div class="main">
        <ul>
          <li>
            血 红 蛋 白:
            <el-input v-model="model.result1" style="width: 180px;"></el-input>
          </li>
          <li>
            谷丙转氨酶:
            <el-input v-model="model.result2" style="width: 180px;"></el-input>
          </li>
          <li>
            空 腹 血 糖:
            <el-input v-model="model.result3" style="width: 180px;"></el-input>
          </li>
          <li>
            甘 油 三 酯:
            <el-input v-model="model.result4" style="width: 180px;"></el-input>
          </li>
          <li>
            肌 酐:
            <el-input v-model="model.result5" style="width: 180px;"></el-input>
          </li>
          <li>
            血 尿 酸:
            <el-input v-model="model.result6" style="width: 180px;"></el-input>
          </li>
          <li>
            谷草转氨酶:
            <el-input v-model="model.result7" style="width: 180px;"></el-input>
          </li>
          <li>
            总 胆 固 醇:
            <el-input v-model="model.result8" style="width: 180px;"></el-input>
          </li>
          <li>
            低密度脂蛋白:
            <el-input v-model="model.result9" style="width: 180px;"></el-input>
          </li>
          <li>
            尿 素 氮 :
            <el-input v-model="model.result10" style="width: 180px;"></el-input>
          </li>
        </ul>
      </div>
    </div>
    <div class="title3-info">
      <h4>三、既往病史</h4>
      <div style="margin-bottom: 10px;">是否患有以下慢性病</div>
      <el-checkbox-group v-model="model.checkList1">
        <el-checkbox label="糖尿病"></el-checkbox>
        <el-checkbox label="高血脂"></el-checkbox>
        <el-checkbox label="高尿酸血症"></el-checkbox>
        <el-checkbox label="高血压"></el-checkbox>
        <el-checkbox label="慢性胃炎"></el-checkbox>
        <el-checkbox label="肺结核"></el-checkbox>
        <el-checkbox label="冠心病"></el-checkbox>
        <el-checkbox label="慢性支气管"></el-checkbox>
        <el-checkbox label="肺气肿"></el-checkbox>
        <el-checkbox label="癌症"></el-checkbox>
      </el-checkbox-group>
    </div>
    <div class="title4-info">
      <h4>四、中医体质调查</h4>
      <el-checkbox-group v-model="model.checkList2">
        <el-checkbox label="喜喝冷饮"></el-checkbox>
        <el-checkbox label="口干舌燥、口臭口苦"></el-checkbox>
        <el-checkbox label="身体经常发热、怕冷"></el-checkbox>
        <el-checkbox label="脾气暴躁易怒"></el-checkbox>
        <el-checkbox label="脸色发红、面红耳赤"></el-checkbox>
        <el-checkbox label="常常便秘且大便干燥"></el-checkbox>
        <el-checkbox label="尿少而色黄"></el-checkbox>
        <el-checkbox label="舌红且有厚黄苔"></el-checkbox>
        <el-checkbox label="面部痤疮"></el-checkbox>
        <el-checkbox label="舌色淡红"></el-checkbox>
        <el-checkbox label="手脚冰冷、怕风、怕冷"></el-checkbox>
        <el-checkbox label="不喜喝水、很少口渴"></el-checkbox>
        <el-checkbox label="常感疲惫"></el-checkbox>
        <el-checkbox label="精神萎靡、脸色苍白"></el-checkbox>
        <el-checkbox label="尿多且色淡、且常腹泻"></el-checkbox>
        <el-checkbox label="怕冷、嗜睡乏力"></el-checkbox>
        <el-checkbox label="不喜喝水，喜热食"></el-checkbox>
        <el-checkbox label="尿多且易腹泻"></el-checkbox>
        <el-checkbox label="性欲减退、手脚冰凉"></el-checkbox>
        <el-checkbox label="气少懒言，脸色苍白"></el-checkbox>
        <el-checkbox label="食欲不振，不喜运动，稍动就头晕目眩或气喘急促"></el-checkbox>
        <el-checkbox label="体型消瘦、脸色苍白"></el-checkbox>
        <el-checkbox label="毛发稀少、健忘、头晕眼花"></el-checkbox>
        <el-checkbox label="月经少，脉搏细而无力"></el-checkbox>
        <el-checkbox label="形体消瘦、心烦气躁"></el-checkbox>
        <el-checkbox label="常渴喜冷饮"></el-checkbox>
        <el-checkbox label="盗汗、手足心发汗冒热"></el-checkbox>
        <el-checkbox label="失眠"></el-checkbox>
        <el-checkbox label="小便黄且舌红、便秘、大便于工作干硬 "></el-checkbox>
        <el-checkbox label="烦闷不乐"></el-checkbox>
        <el-checkbox label="时有叹气"></el-checkbox>
        <el-checkbox label="喉部有异物感"></el-checkbox>
        <el-checkbox label="胸胁胀满"></el-checkbox>
        <el-checkbox label="多愁善感"></el-checkbox>
        <el-checkbox label="经常过敏"></el-checkbox>
      </el-checkbox-group>
    </div>
    <div class="title5-info">
      <h4>五、以下内容请在主管医师指导下填写</h4>

      <div class="status1">
        <div style="margin-bottom: 10px;">1.骨折的稳定性(30分)</div>
        <el-radio v-model="model.radio24" label="1">(21-30分)稳定性骨折（相当于AO的A型）</el-radio>
        <el-radio v-model="model.radio24" label="2">(11-20分)较稳定性骨折（相当于AO的B型）</el-radio>
        <el-radio v-model="model.radio24" label="3">(1-10分)不稳定性骨折（相当于AO的C型）</el-radio>
        <el-radio v-model="model.radio24" label="4">(0分)波及关节内的极不稳定骨折或有骨缺损</el-radio>
      </div>
      <div class="status2">
        <div style="margin-bottom: 10px;">2.固定的可靠性(40分)</div>
        <el-radio v-model="model.radio25" label="1">(31-40分)坚强固定，可立即负重</el-radio>
        <el-radio v-model="model.radio25" label="2">(21-30分)术后能达到借助支具功能主动运动</el-radio>
        <el-radio v-model="model.radio25" label="3">(11-20分)术中即能被动运动</el-radio>
        <el-radio v-model="model.radio25" label="4">(1-10分)能对抗肢体重力但不宜对抗助力</el-radio>
        <el-radio v-model="model.radio25" label="5">(0分)维持对位，需辅助外固定，牵引等</el-radio>
      </div>
      <div class="status3">
        <div style="margin-bottom: 10px;">3.软组织的完整性(30分)</div>
        <el-radio v-model="model.radio26" label="1">(21-30分)合理手术入路（创伤少）韧带解剖对合修复牢固</el-radio>
        <el-radio v-model="model.radio26" label="2">(11-20分)关节韧带缝合，术中部分对抗张力</el-radio>
        <el-radio v-model="model.radio26" label="3">(1-10分)关节韧带缝合，术中不能对抗张力</el-radio>
        <el-radio v-model="model.radio26" label="4">(0分)软组织损伤严重或有缺损或有感染或行血管、神经修复</el-radio>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      model: {
        name: "",
        age: "",
        height: "",
        weight: "",
        radio: "",
        radio1: "",
        radio2_1: "",
        radio2_2: "",
        radio2_3: "",
        radio3: "",
        radio4: "",
        radio5: "",
        radio6: "",
        radio6_1: "",
        radio7: "",
        radio8: "",
        radio9: "",
        radio10: "",
        radio11: "",
        radio12: "",
        radio13: "",
        radio14: "",
        radio15: "",
        radio16: "",
        radio17: "",
        radio18: "",
        radio19: "",
        radio20: "",
        radio21: "",
        radio22: "",
        radio23: "",
        result1: "",
        result2: "",
        result3: "",
        result4: "",
        result5: "",
        result6: "",
        result7: "",
        result8: "",
        result9: "",
        result10: "",
        checkList1: [],
        checkList2: [],
        radio24: "",
        radio25: "",
        radio26: ""
      },
      isShow: false
    };
  },
  methods: {
    changeLabel() {
      this.isShow = !this.isShow;
    },
    changeNoLabel() {
      this.isShow = false;
    }
  }
};
</script>

<style scoped>
* {
  color: black;
  padding: 0;
  text-align: left;
}
.container {
  width: 95%;
  height: 100%;
  margin-left: 5%;
}
.container h2 {
  text-align: center;
}
.index-title {
  width: 100%;
  height: 80px;
}
.el-input {
  width: 100%;
  margin-bottom: 3px;
}
/* .el-input .el-input__inner {
  /*border: none;
  height: 15px;
} */

.title1-info,
.title2-info,
.title3-info,
.title4-info {
  margin-left: 10px;
}
.title3 {
  font-size: 14px;
  text-align: center;
}
.title1-info h4 {
  margin-top: 10px;
}
.yes {
  display: none;
}
.yes_click {
  display: inline;
  margin-left: -20px;
}
.main {
  width: 100%;
  margin-top: -20px;
  font-size: 14px;
}

.main ul li {
  list-style: none;
}
.el-radio {
  height: 30px;
}
.el-checkbox {
  height: 40px;
}
/* .el-input__inner {
  border: none;
} */
</style>
