# web<html>
<head>
<title>vue ʱ��</title>
</head>
<body>
<div id='app'>
{{date | dateStr}}
</div>
<script src="https://cdn.bootcss.com/moment.js/2.24.0/moment.js"></script>
<script src="https://cdn.bootcss.com/vue/2.6.10/vue.common.dev.js"></script>
<script type="text/Javascript">
Vue.filter('dateStr',function(){
return moment().format('YYYY-MM-DD HH-mm-ss')
})
 new Vue({
 el:'#app',
data(){
return{
date:new Date()
}}
})
</script>
</body>
</html>
