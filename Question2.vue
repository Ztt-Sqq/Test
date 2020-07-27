<template>
  <div class="box">
    <h2>{{title}}</h2>
    <div class="info">
      <ul>
        <li>
          <label>姓名：</label>
          <el-input style="width:100px" v-model="model.info_name"></el-input>
          <label>年龄：</label>
          <el-input style="width:100px" v-model="model.info_age"></el-input>
        </li>
        <li>
          <label>身高：</label>
          <el-input style="width:100px" v-model="model.info_height"></el-input>
          <label>体重：</label>
          <el-input style="width:100px" v-model="model.info_weight"></el-input>
        </li>
      </ul>
    </div>

    <!-- 一般情况 -->
    <div class="main">
      <span>{{topic[0]}}</span>
      <!-- 1 -->
      <ul>
        <li>{{ questionList[0].question }}</li>
        <li>
          <el-radio-group v-model="model.radio1">
            <el-radio
              v-for="(item,index) in questionList[0].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>
        <!-- </ul> -->

        <!-- 2 -->
        <!-- <ul> -->
        <li>{{ questionList[1].question }}</li>
        <li>
          <el-radio-group v-model="model.radio2">
            <el-radio
              v-for="(item,index) in questionList[1].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>
        <!-- </ul> -->

        <!-- 3 -->
        <!-- <ul> -->
        <li>{{ questionList[2].question }}</li>
        <li class="radio3_li" v-for="(item,index) in questionList[2].choices" :key="item.id">
          {{ item }}：
          <el-input style="width: 50px" v-model="model.radio3[index]"></el-input>
        </li>
        <!-- <li class="radio3_li">
          <label>{{ questionList[2].choices[0] }}：</label>
          <el-input style="width: 15%" v-model="model.radio3_1"></el-input>
          <label>{{ questionList[2].choices[1] }}：</label>
          <el-input style="width: 15%" v-model="model.radio3_2"></el-input>
          <label>{{ questionList[2].choices[2] }}：</label>
          <el-input style="width: 15%" v-model="model.radio3_3"></el-input>
        </li>-->

        <!-- 4 -->
        <li>{{ questionList[3].question }}</li>
        <li>
          <el-radio-group v-model="model.radio4">
            <el-radio
              v-for="(item,index) in questionList[3].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>

        <!-- 5 -->
        <li>{{ questionList[4].question }}</li>
        <li>
          <el-radio-group v-model="model.radio5">
            <el-radio
              v-for="(item,index) in questionList[4].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>

        <!-- 6 -->
        <li>{{ questionList[5].question }}</li>
        <li>
          <el-radio-group v-model="model.radio6">
            <el-radio
              v-for="(item,index) in questionList[5].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>

        <!-- 7 -->
        <li>{{ questionList[6].question }}</li>
        <li>
          <el-radio-group v-model="model.radio7">
            <el-radio label="yes" @change="changeLabel">
              {{ questionList[6].choices[0] }}
              <label :class="isShow? 'label_yes':'label'">
                有哪些
                <el-input v-model="model.radio7_1" style="width: 80%"></el-input>
              </label>
            </el-radio>
            <el-radio label="no" @change="changeLabelN">{{ questionList[6].choices[1] }}</el-radio>
          </el-radio-group>
        </li>

        <!-- 8 -->
        <li>{{ questionList[7].question }}</li>
        <li>
          <el-radio-group v-model="model.radio8">
            <el-radio
              v-for="(item,index) in questionList[7].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>
      </ul>
    </div>

    <!-- 二化验检查结果 -->
    <div class="main">
      <span>{{ topic[1] }}</span>
      <ul class="main2_ul">
        <li class="main2_li" v-for="(item,index) in result" :key="item.id">
          {{ item }}：
          <el-input style="width: 200px" v-model="model.resultList[index]"></el-input>
        </li>
      </ul>
    </div>

    <!-- 三既往病史 -->
    <div class="main">
      <span>{{ topic[2] }}</span>
      <ul>
        <li class="main3_li" v-for="(item,index) in medical" :key="index">
          <el-checkbox v-model="model.checkList1[index]">{{ item }}</el-checkbox>
        </li>
      </ul>
    </div>

    <!-- 四中医体质调查 -->
    <div class="main">
      <span>{{ topic[3] }}</span>
      <ul>
        <li class="main4_li" v-for="(item,index) in examine" :key="index">
          <el-checkbox v-model="model.checkList2[index]">{{ item }}</el-checkbox>
        </li>
      </ul>
    </div>

    <!-- 以下内容 -->
    <div class="main">
      <span>{{ topic[4] }}</span>
      <ul>
        <li v-for="(item,index) in operation" :key="index">
          {{ item }}
          <el-input style="width: 180px" v-model="model.reason[index]"></el-input>
        </li>
        <li>骨科运动康复安全性评定表：</li>
        <!-- 5-1 -->
        <li>{{ questionList[8].question }}</li>
        <li>
          <el-radio-group v-model="model.radio9">
            <el-radio
              v-for="(item,index) in questionList[8].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>

        <!-- 5-2 -->
        <li>{{ questionList[9].question }}</li>
        <li>
          <el-radio-group v-model="model.radio10">
            <el-radio
              v-for="(item,index) in questionList[9].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>

        <!-- 5-3 -->
        <li>{{ questionList[10].question }}</li>
        <li>
          <el-radio-group v-model="model.radio11">
            <el-radio
              v-for="(item,index) in questionList[10].choices"
              :key="item.id"
              :label="index"
            >{{ item }}</el-radio>
          </el-radio-group>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "骨科术后管理问卷",
      isShow: false,
      topic: [
        "一、一般情况",
        "二、化验检查结果",
        "三、既往病史",
        "四、中医体质调查",
        "五、以下内容请在主管医师指导下填写"
      ],
      questionList: [
        {
          question: "1.您的口味与周围的人相比如何？（单选）",
          choices: ["A.很淡", "B.略淡", "C.相同", "D.略咸"]
        },
        {
          question: "2.您每顿饭吃几成饱？（单选）",
          choices: ["A.六成饱", "B.七成饱", "C.八成饱", "D.九成饱", "E.过饱"]
        },
        {
          question: "3.您三餐的饮食分配比例？（按十份算）",
          choices: ["早餐", "午餐", "晚餐"]
        },
        {
          question:
            "4.您饮食品种是否多样化？（每天多于12种，每周多于25种算多样）",
          choices: ["A.是", "B.否"]
        },
        {
          question: "5.您每天大约饮水量（   ）ml。",
          choices: ["A.小于1000", "B.1000-1500", "C.1500-2000", "D.大于2000"]
        },
        { question: "6.您目前食欲如何", choices: ["A.良好", "B.欠佳"] },
        { question: "7.是否服用膳食补充剂", choices: ["A.是", "B.否"] },
        { question: "8.大便情况", choices: ["A.正常", "B.便秘"] },
        {
          question: "1、(30分)骨折的稳定性:",
          choices: [
            "A.(21-30分)稳定性骨折（相当于AO型的A型）",
            "B.(11-20分)较稳定性骨折（相当于AO的B型）",
            "C.(1-10分)不稳定性骨折（相当于AO的C型）",
            "D.(0分)波及关节内的极不稳定骨折或有骨缺损"
          ]
        },
        {
          question: "2、(40分)固定的可靠性:",
          choices: [
            "A.(31-40分)坚强固定，可立即负重",
            "B.(21-30分)术后能达到借助支具功能主动运动",
            "C.(11-20分)术中即能被动运动",
            "D.(1-10分)能对抗肢体重力但不宜对抗助力",
            "E.(0分)维持对位，需辅助外固定，牵引等"
          ]
        },
        {
          question: "3、(30分)软组织的完整性:",
          choices: [
            "A.(21-30分)合理手术入路（创伤少）韧带解剖对合修复牢固",
            "B.(11-20分)关节韧带缝合，术中部分对抗张力",
            "C.(1-10分)关节韧带缝合，术中不能对抗张力",
            "D.(0分)软组织损伤严重或有缺损或有感染或行血管、神经修复"
          ]
        }
      ],
      result: [
        "血红蛋白",
        "血尿酸",
        "谷丙转氨酶",
        "谷草转氨酶",
        "空腹血糖",
        "总胆固醇",
        "甘油三酯",
        "低密度脂蛋白",
        "肌酐",
        "尿素氮"
      ],
      medical: [
        "糖尿病",
        "高血脂",
        "高尿酸血症",
        "高血压",
        "慢性胃炎",
        "肺结核",
        "冠心病",
        "慢性支气管",
        "肺气肿",
        "癌症"
      ],
      examine: [
        "喜喝冷饮",
        "口干舌燥、口臭口苦",
        "身体经常发热、怕冷",
        "脾气暴躁易怒",
        "脸色发红、面红耳赤",
        "常常便秘且大便干燥",
        "尿少而色黄",
        "舌红且有厚黄苔",
        "面部痤疮",
        "舌色淡红",
        "手脚冰冷、怕风、怕冷",
        "不喜喝水、很少口渴",
        "常感疲惫",
        "精神萎靡、脸色苍白",
        "尿多且色淡、且常腹泻",
        "怕冷、嗜睡乏力",
        "不喜喝水，喜热食",
        "尿多且易腹泻",
        "性欲减退、手脚冰凉",
        "气少懒言，脸色苍白",
        "食欲不振，不喜运动，稍动就头晕目眩或气喘急促",
        "体型消瘦、脸色苍白",
        "毛发稀少、健忘、头晕眼花",
        "月经少，脉搏细而无力（限女性填写）",
        "形体消瘦、心烦气躁",
        "常渴喜冷饮",
        "盗汗、手足心发汗冒热",
        "失眠",
        "小便黄且舌红、便秘、大便于工作干硬",
        "烦闷不乐",
        "时有叹气",
        "喉部有异物感",
        "胸胁胀满",
        "多愁善感",
        "经常过敏"
      ],
      operation: ["手术原因：", "手术方式："],
      model: {
        info_name: "",
        info_age: "",
        info_height: "",
        info_weight: "",
        radio1: "",
        radio2: "",
        radio3: [],
        radio4: "",
        radio5: "",
        radio6: "",
        radio7: "",
        radio7_1: "",
        radio8: "",
        resultList: [],
        checkList1: [],
        checkList2: [],
        reason: [],
        radio9: "",
        radio10: "",
        radio11: ""
      }
    };
  },
  methods: {
    changeLabel() {
      this.isShow = !this.isShow;
    },
    changeLabelN() {
      this.isShow = false;
      this.model.radio7_1 = "";
    },
  }
};
</script>

<style scoped>
* {
  padding: 0;
  line-height: 32px;
}
li {
  list-style-type: none;
  margin-bottom: 5px;
}
span {
  font-size: 18px;
  font-weight: 700;
}

/* main_1 */
.main {
  text-align: left;
  padding-left: 3%;
  padding-right: 3%;
}
.radio3_li {
  display: inline;
  font-size: 14px;
  color: #606266;
  margin-left: 3%;
}
.label {
  display: none;
}
.label_yes {
  display: inline;
}
/* main_2 */
.main2_li {
  font-size: 14px;
  color: #606266;
}
.main3_li {
  display: inline-block;
  margin-right: 20px;
}
.main4_li {
  margin-right: 15%;
}
</style>