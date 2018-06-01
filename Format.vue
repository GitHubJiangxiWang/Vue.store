<!DOCTYPE html>
<html lang = "en">
<head>
<meta name = "viewport" content = "width = device-width, initial-scale = 1.0" ></meta>
<meta charset = "UTF-8" ></meta>
<meta http-equiv = "X-UA-Compatible" content = "id=edge" ></meta>
<meta name = "keywords" content = "HTML,ASP,PHP,SQL">
<meta http-equiv = "charset" content = "GB2312" >
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
<script src = "https://unpkg.com/vuex@3.0.1/dist/vuex.js" ></script>
<script src = "https://unpkg.com/vue@2.5.16/dist/vue.js" ></script>
<title>计算属性computed</title>
</head>
<style>

body { padding-left: 50px;}

* { font-family: 楷书; color: #8d0595; }

input {
	border: 2px solid #00CCFF;
	border-radius: 5px;
	padding: 2px 0 2px 12px;
	box-shadow: 5px 5px 3px lightgreen;
	margin:0 10px 0 10px;
}

.electricCost button {
	width: 80px;
	height: 80px;
	border-radius: 40px;
	background-color: #f3ff10;
	font-family: 隶书;
	font-size: 30px;
}

.myFriend *{
	color: black;
	font-size: 20px;
}

.myFriend button {
	width: 200px;
	height: 60px;
	border-radius: 8px;
	background-color: yellow;
	font-family: 行书;
	font-size: 30px;
}
</style>

<body>
<div id = "youNameId" >
	<div class = "myFriend">
		<p>快，告诉我，你是谁，我告诉你，你在哪里，哼，不信？试试不就知道了？哦，对了，你是谁？你在哪里？先告诉我呗？</p>
		<input type = "text" id = "myFriendName" ><button v-on:click = "getFriendName" type = "text" >提交大名</button>
		<div v-if = "friendName === '开始'" >
			<p>别看了，快输入你的名字，真的是，过个六一还这么6~<p>
		</div>
		<div v-else-if = "friendName === '张福建'" >
			<p>坑逼，除了你会输入我的名字，也就没有谁了，哼，小朋友，我爱你~哦，忘记告诉你了，今天是六一~！</p>
		</div>
		<div v-else-if = "friendName === '陈淑珍'">
			<p>有没有人曾告诉你，我很爱你~！</p>
			<img src = "./axin.gif">
		</div>
		<div v-else-if = "friendName === '陈'">
			<p>小朋友，以为我不知道是你吗？嗯哇~我爱你~！</p>
			<img src = "./axin.gif">
		</div>
		<div v-else-if = "friendName === '罗金华'" >
			<p>小朋友，98Karar送你，让你看到前面的美女，这样，你就能看到你的女朋友了，六一快乐~~</p>
		</div>
		<div v-else-if = "friendName === '马水'" >
			<p>你辣么帅，福建才喜欢你的，你以为我搞基吗？哈哈，要不是今天是六一，我才读六年级，就娶你了。^_^，这你也信，六一快乐~</p>
		</div>
		<div v-else-if = "friendName === '俞马水'" >
			<p>因为我刚好遇见你，天打雷劈没毛病，转角遇见小毛驴，六一麻将吃个鸡~</p>
		</div>
		<div v-else-if = "friendName === '丘小'" >
			<p>最帅的就是你了，要是六一能坐上你的车兜具风什么的，再好不过了，然后，然后？还能有什么，过六一啊~</p>
		</div>
		<div v-else-if = "friendName === '邱小'" >
			<p>最帅的就是你了，要是六一能坐上你的车兜具风什么的，再好不过了，然后，然后？还能有什么，过六一啊~</p>
		</div>
		<div v-else-if = "friendName === '邱凌宇'" >
			<p>最帅的就是你了，要是六一能坐上你的车兜具风什么的，再好不过了，然后，然后？还能有什么，过六一啊~</p>
		</div>
		<div v-else-if = "friendName === '大傻'" >
			<p>嗯，你没有看错，你回到了你的六一，还等什么，给糖给人家啊！</p>
		</div>
		<div v-else-if = "friendName === '罗胖子'" >
			<p>老王隔壁在练腰，别看了，你没有，对，小朋友怎么会有猪腰？给我一根棉花糖，我能给你一个水桶！给你水桶干什么？！过六一啊！</p>
		</div>
		<div v-else-if = "friendName === '丘胖子'" >
			<p>你们不懂98Karat没有对手，哼，镜头开开来，只能看到小朋友，一枪一个小朋友，送他们回家过六一~</p>
		</div>
		<div v-else-if = "friendName === '张阳亮'" >
			<p>哦，你是我哥，对不对？嗯，对的，我们都是大朋友了，不过还是可以吃一个糖，哈哈~</p>
		</div>
		<div v-else-if = "friendName === '张辉煌' || friendName === '辉煌'" >
			<p>哦，辉煌同学，哈哈，六一快乐~！</p>
		</div>
		<div v-else-if = "friendName === '周邵平' || friendName === '邵平'" >
			<p>哦，原来是你，哈哈，六一快乐~！</p>
		</div>
		<div v-else-if = "friendName === '张三禄'" >
			<p>爸，你好，过六一了，可以吃糖了~</p>
		</div>
		<div v-else>
			<p>O(∩_∩)O哈哈~，又想带我去哪里？去浪漫的土耳其？还是东京卖烧饼?让我们唱首歌吧~五星红旗迎风飘扬，哦，不对，你在过六一吗？！哼，小猪佩琪，ヾ(￣▽￣)Bye~Bye~~</p>
			<p>哦，大朋友 ，六一快乐~嗯，记得发糖~</p>
			<img src = "./zhuang.gif">
		</div>
		
	</div>
	
	<hr>
	<div class = "electricCost" v-show = "countPower" >	
		只看到多少匹？切换模式！<button v-on:click = "countPowerBTN" >按匹算~</button>
		<h5>输入功率，帮你计算大概的价钱哟，算错过来打我！来吧~</h5>
		<select v-model = "electricSelected" >
			<option v-for = "electric in electrics" v-bind:value = "electric.name" >{{ electric.name }}</option>
		</select>
		功率： <input type = "number" v-model = "ePower" step = "50" >
		{{ electricSelected }}=>用几个小时:<input type = "number" v-model = "eHour" step = "0.5">
		电费价格:  <input type = "number" v-model = "eMoney" step = "0.1">
		<p id = "electricCost" >{{ electricCost }}</p>
	</div>
	
	<div class = "electricCost" v-show = "countHorse" >
		只看到多少千瓦？<button v-on:click = "countHorseBTN" >按这里~</button>
		<h5>输入匹数，帮你计算大概的电费哟，算错过来打我！来呀~</h5>
		<select v-model = "electricSelected" >
			<option v-for = "electric in electrics" v-bind:value = "electric.name" >{{ electric.name }}</option>
		</select>	
			匹数：<input type = "number" v-model = "eHorsePower" step = "0.1" >
			{{ electricSelected }} =>用几个小时：<input type = "number" v-model = "eHorseHour" step = "0.5">
			电费价格：<input type = "number" v-model = "eHorseMoney" step = "0.1">
		<p id = "electricHorseCost" >{{ electricHorseCost }}</p>
	</div>
	<hr>
	<div v-show = "format">
		<p>又根据公式</p>
		<p>1度电 = 1千瓦 = 3 600 000 焦耳</p>
		<p>1匹 = 0.735 千瓦 </p>
	</div>
	<input type = "number" v-model = "celsius" >摄氏度 = <input type = "number" v-model = "fahrenheit" >华氏度 
	<br><br>
	<hr>
	<div>
		根据公式：<br>
		<p>华氏 = 摄氏 × 1.8 + 32</p>
		<p>摄氏 = (华氏-32) ÷ 1.8</p>
	</div>
	<p id = "info" >
		<span id = "celsius" >20.000摄氏度</span> = <span id = "fahrenheit" >68.000华氏度</span>
	</p>
	<hr>
	
	
</div>	
</body>

<script>

var Vue = new Vue({
	el: '#youNameId',
	data: {
		celsius: 20,
		fahrenheit: 68,
		electrics: [
			{ name: '冰箱' },
			{ name: '空调' },
			{ name: '电风扇'},
			{ name: '吹风机' },
			{ name: '洗衣机'},
			{ name: '其它' }
		],
		electricSelected: '冰箱',
		ePower: 2000,
		eHour: 1,
		eMoney: 0.86,
		electricCost: 1.72,
		eHorsePower: 1,
		electricHorseCost: 0.6321,
		eHorseHour: 1,
		eHorseMoney: 0.86,
		countPower: true,
		countHorse: false,
		format: true,
		friendName: '开始'
	},
	methods: {
		countPowerBTN () {
			this.countPower = false
			this.countHorse = true
		},
		countHorseBTN () {
			this.countHorse = false
			this.countPower = true
		},
		getFriendName () {
			this.friendName = document.getElementById('myFriendName').value
		}
		
	},
	watch: {
		celsius: function (value) {
			this.celsius = value;
			this.fahrenheit = this.celsius * 1.8 + 32;
		},
		fahrenheit: function (value) {
			this.fahrenheit =  value;
			this.celsius = (this.fahrenheit - 32) / 1.8;
		},
		ePower: function (value) {
			this.ePower = value;
			this.electricCost = (this.ePower * this.eHour * this.eMoney)/1000;
		},
		eHour: function (value) {
			this.eHour = value;
			this.electricCost = (this.eHour * this.ePower * this.eMoney)/1000;
		},
		eMoney: function (value) {
			this.eMoney = value;
			this.electricCost = (this.eMoney * this.ePower * this.eHour)/1000;
		},
		eHorsePower: function (value) {
			this.eHorsePower = value;
			this.electricHorseCost = (this.eHorsePower * 735 * this.eHorseHour * this.eHorseMoney)/1000;
		},
		eHorseHour: function (value) {
			this.eHorseHour = value;
			this.electricHorseCost = (this.eHorsePower * 735 * this.eHorseHour * this.eHorseMoney)/1000;
		},
		eHorseMoney: function (value) {
			this.eHorseMoney = value;
			this.electricHorseCost = (this.eHorsePower * 735 * this.eHorseHour * this.eHorseMoney)/1000;
		}
	}
});

Vue.$watch('celsius', function (newValue, oldValue) {
	// document.getElementById('info').innerHTML = "计算的是：" + newValue + "摄氏度；" + "刚才是：" + oldValue + "摄氏度"
	document.getElementById('celsius').innerHTML = (this.celsius).toFixed(3) + '摄氏度';
	document.getElementById('fahrenheit').innerHTML = (this.fahrenheit).toFixed(3) + '华氏度';
	document.getElementById('electricCost').innerHtml = this.electricCost + '元';
	document.getElementById('electricHorseCost').innerHTML = this.electricHorseCost + '元';
})

</script>

</html>
