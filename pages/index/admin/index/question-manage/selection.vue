<template>
  <div>
      <QuestionDetail :options="options"  :questionType="questionType"/>
  </div>
</template>
<script setup>
import axios from "axios"
useHead({
title:"题库细则"
})

const questionType=ref("judgement")
const options=ref([])
const { data, pending, error, refresh } = await useFetch('http://localhost:8888/questionBanks',{
  onRequest({ request, options }) {
    // 设置请求头
  },
  onRequestError({ request, options, error }) {
    // 处理请求错误
    ElMessage.error(error.message)
  },
  onResponse({ request, response }) {
    // 处理响应数据
    options.value=response._data.options
    useState('options', () => options.value)

  },
  onResponseError({ request, response, options }) {
    // 处理响应错误
    ElMessage.error(error.message)
  }
})


// const options = [
// {
//   value: 'Option1',
//   label: '马克思主义原理',
// },
// {
//   value: 'Option2',
//   label: '毛泽东思想',
// },
// {
//   value: 'Option3',
//   label: '习近平新思想',
// },
// ]


// 获取题目列表
// const tableData=shallowRef([])
// onMounted(() => {
// axios.get(`http://localhost:8888/get/allquestion?name=${options.value[0].label}`
// ).then(response => {
// // 请求成功，处理响应
// console.log('获取的数据:', response.data);
// tableData.value = response.data;
// // console.log(tableData);
// }).catch(error => {
// // 处理请求错误
// ElMessage.error('获取题目列表失败');
// console.error('请求失败:', error);
// })

// })



// const tableData= [
//   {
//     id: '1',
//     title: '垄断利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '低于平均利润 ',
//     optionB: '等于平均利润',
//     optionC: '超过平均利润',
//     optionD: '等于生产价格 ',
//     optionE: 'xxxxxxxxxxxxxx ',
//     Anumber:23,
//     Bnumber:177,
//     Cnumber:61,
//     Dnumber:34,
//     Enumber:62,
//     correctAnswer: 'C',
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '2',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     correctAnswer: 'C',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '3',
//     title: '苏联解体、苏东剧变的最根本原因是（）方向出了问题。  ',
//     optionA: '经济',
//     optionB: '政治',
//     optionC: '科学文化',
//     optionD: '教育',
//     correctAnswer: 'B',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     correctAnswer: 'C',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '4',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     correctAnswer: 'C',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
    
//   },
//   {
//     id: '5',
//     title: '客观世界的万事万物都处于普遍联系之中，这属于（）的观点。',
//     optionA: '形而上学唯物主义',
//     optionB: '唯物辩证法',
//     optionC: '形而上学唯心主义',
//     optionD: '唯心主义历史观',
//     correctAnswer: 'B',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '6',
//     title: '（）标志着简单商品生产发展到资本主义商品生产的新阶段。',
//     optionA: '劳动力成为商品  ',
//     optionB: '资本主义制度的确立 ',
//     optionC: '私人劳动和社会劳动矛盾的解决 ',
//     optionD: '商品完成“惊险的跳跃”  ',
//     correctAnswer: 'A',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '7',
//     title: '在展望未来社会的问题上，马克思主义与空想社会主义的根本区别是（）。',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '8',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '是否坚持科学的立场、观点、方法   ',
//     optionB: '展望的目的和动机是否正确 ',
//     optionC: '是否有预见未来社会详细特征 ',
//     optionD: '是否有预见未来社会详细特征  ',
//     correctAnswer: 'A',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '9',
//     title: '共产主义社会实现的根本条件是（）。',
//     optionA: '国家垄断资本主义的形成',
//     optionB: '人类理性的高度觉醒',
//     optionC: '人类19世纪创造的优秀理论成果',
//     optionD: '生产力的高度发达',
//     correctAnswer: 'D',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '10',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '11',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '12',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '13',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '14',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '15',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '16',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '17',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   {
//     id: '18',
//     title: '垄断以前在农村，秸秆对农民来说几乎是一个毫无价值的东西，往往通过焚烧来处理，而随着新能源研究的推进，秸秆作为发电和制沼的原料，其价值在某种程度上甚至超过了粮食。这说明（）。利润是垄断资本家凭借其在社会生产和流通中的垄断地位而获得的（）的高额利润',
//     optionA: '客体的价值不具有确定性  ',
//     optionB: '不同主体的评价创造了不同价值 ',
//     optionC: '价值是实践基础上确立的主体与客体之间一种创造性关系 ',
//     optionD: '价值随主体变化，而变化与客体本身无关  ',
//     correctAnswer: 'C',
//     Anumber:23,
//     Bnumber:37,
//     Cnumber:61,
//     Dnumber:134,
//     type: '单选题',
//     creationTime:'2023-08-04',
//     lastModified:'2023-05-06',
//     modifiedBy:'hhh',
//     createdBy:'hhc'
//   },
//   ]
</script>
<style>
</style>
