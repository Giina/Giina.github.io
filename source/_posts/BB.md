---
title: BB
lang: zh
date: 2018-11-07 11:29:52
tags: ['工具']
---

<link rel="stylesheet" type="text/css" href="http://unpkg.com/iview/dist/styles/iview.css">
<script type="text/javascript" src="http://vuejs.org/js/vue.min.js"></script>
<script type="text/javascript" src="http://unpkg.com/iview/dist/iview.min.js"></script>
<style>
#app{
text-align:center;
}
.ivu-card {
float:left;
}</style>
<div id="app">
  <Layout>
    <Header>计算器</Header>
    <Content>
      <Card style="width:100%">
        <div style="text-align:center">
          <i-input v-model="targetVal">
            <span slot="prepend">￥</span>
            <i-button slot="append" type="warning" @click="goC">计算</i-button>
          </i-input>
        </div>
      </Card>
      <Card style="width:50%">
        <h1>方案一</h1>
        <i-table :columns="columns1" :data="data1"></i-table>
      </Card>
      <Card style="width:50%">
        <h1>方案二</h1>
        <i-table :columns="columns1" :data="data2"></i-table>
      </Card>
    </Content>
    <Footer>开发者不对计算结果负责，如有疑问请咨询人事部门同事，<a target="_blank" href="http://salarycalculator.sinaapp.com/">方案一计算方法来自：上海市五险一金及税后工资计算器</a></Footer>
  </Layout>
</div>
<script>
new Vue({
el: '#app',
data: {
targetVal: '10000',
names:['养老保险金','医疗保险金','失业保险金','住房公积金','工伤保险金','生育保险金','税后月薪'],
columns1: [
{
title: '条目',
key: 'name'
},
{
title: '个人',
key: 'personal'
},
{
title: '单位',
key: 'company'
}
],
data1: [
{
name:'养老保险金',
personal:'x',
company:'x'
},
{
name:'医疗保险金',
personal:'x',
company:'x'
},
{
name:'失业保险金',
personal:'x',
company:'x'
},
{
name:'住房公积金',
personal:'x',
company:'x'
},
{
name:'工商保险金',
personal:'0',
company:'x'
},
{
name:'生育保险金',
personal:'0',
company:'x'
},
{
name:'税后月薪',
personal:'x',
company:'x'
},
{
name:'个人所得税',
personal:'x',
company:'x'
}
],
data2: [
{
name:'养老保险金',
personal:'400(8%)',
company:'1000(20%)'
},
{
name:'医疗保险金',
personal:'100(2%)',
company:'475(9.5%)'
},
{
name:'失业保险金',
personal:'25(0.5%)',
company:'25(0.5%)'
},
{
name:'住房公积金',
personal:'350(7%)',
company:'350(7%)'
},
{
name:'工伤保险金',
personal:'0',
company:'10(0.2%)'
},
{
name:'生育保险金',
personal:'0',
company:'50(1%)'
},
{
name:'税后月薪',
personal:'4125',
company:'x'
},
{
name:'个人所得税',
personal:'0',
company:'x'
}]
},
methods: {
goC: function () {
const vm=this
if(vm.targetVal){
vm.data1[0].personal=Math.ceil(+vm.targetVal*8/100)+'(8%)'
vm.data1[0].company=Math.ceil(+vm.targetVal*20/100)+'(20%)'
vm.data1[1].personal=Math.ceil(+vm.targetVal*2/100)+'(2%)'
vm.data1[1].company=Math.ceil(+vm.targetVal*9.5/100)+'(9.5%)'
vm.data1[2].personal=Math.ceil(+vm.targetVal*0.5/100)+'(0.5%)'
vm.data1[2].company=Math.ceil(+vm.targetVal*0.5/100)+'(0.5%)'
vm.data1[3].personal=Math.ceil(+vm.targetVal*7/100)+'(7%)'
vm.data1[3].company=Math.ceil(+vm.targetVal*7/100)+'(7%)'
vm.data1[4].company=Math.ceil(+vm.targetVal*0.2/100)+'(0.2%)'
vm.data1[5].company=Math.ceil(+vm.targetVal*1/100)+'(1%)'

let after4=+vm.targetVal*82.5/100-5000
let taxCount=getTaxCount(after4)

vm.data1[6].personal=after4-taxCount+5000

vm.data1[7].personal=taxCount

vm.data2[6].personal=+vm.data2[6].personal+Math.floor((vm.targetVal-5000)*(95.14/100))

}else{}
}
}
})

function getTaxCount(after4){
const taxLevel=[{top:80000,percent:45/100},{top:55000,percent:35/100},{top:35000,percent:30/100},{top:25000,percent:25/100},{top:12000,percent:20/100},{top:3000,percent:10/100},{top:0,percent:3/100}]
let taxCount=0

for(let i=0;i<taxLevel.length;i++){
if(after4>taxLevel[i].top){
taxCount+=Math.floor((after4-taxLevel[i].top)*taxLevel[i].percent)
for(let j=i+1;j<taxLevel.length;j++){
taxCount+=Math.floor((taxLevel[j-1].top-taxLevel[j].top)*taxLevel[j].percent)
}
break;
}
}

return taxCount
}
</script>