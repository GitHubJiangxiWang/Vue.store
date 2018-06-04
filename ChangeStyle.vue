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
<title>颜色切换</title>
</head>

<style type = "text/css">


ol li {
	list-style: none;
	margin: 0 5px;
	padding: 0;
	width: 100px;
	color: cyan;
	height: 50px;
	float: left;
	text-align: center;
	line-height: 40px;
	border-radius: 5px;
	background: lightgreen;
}

.myolli {
	height: 50px;
}


.active {
	background: linear-gradient(30deg,red,blue,cyan,green,navy,lightgreen);
}

.a {
	color: blue;
}

.d {
	font-size: 50px;
}

.b {
	font-size: 10px;
}

</style>

<body>
<div id = "youNameId" >
	<shubiao></shubiao>
</div>	
</body>

<script>

Vue.component('shubiao',{
	template:
	`
		<div>
			<div>
				<h3>Let's see it.</h3>
				<div class = "myolli">
					<ol>
						<li v-for = "(colorer,index) in colorers" v-bind:class = "{ active:index == isActive }" v-bind:key = "colorer.index" v-bind:id = "colorer.index" @mouseenter = "entercolor(index)" @mouseleave = "leavecolor(index)" >{{ colorer.name }}</li>
					</ol>
				</div>
				<div v-show = "showOne" >
					Content show one.
				</div>
				<div v-show = "showTwo" >
					Content show two.
				</div>
				<div v-show = "showThree" >
					Content show three.
				</div>
			</div>
			<hr style = "border: 2px solid blue;">
			<br>
			<div v-bind:class = "[first,isShow ? '' : third]" >
				<p>div content</p>
			</div>
		</div>	
	`,
	data: function (){
		return {
			colorers: [
				{ name: 'colorer1' },
				{ name: 'colorer2' },
				{ name: 'colorer3' }
			],
			isShow: false,
			third: 'd',
			first: 'a',
			isActive: 0,
			showOne: true,
			showTwo: false,
			showThree: false,
		}
	},
	methods: {
		entercolor: function (index) {
			this.isActive = index;
			if (this.isActive == 2) {
				this.showOne = false;
				this.showTwo = false;
				this.showThree = true;
			} else if (this.isActive == 1) {
				this.showOne = false;
				this.showTwo = true;
				this.showThree = false;
			} else if (this.isActive == 0) {
				this.showOne = true;
				this.showTwo = false;
				this.showThree = false;
			}
		},
		leavecolor: function (index) {
			var self = this;
			setTimeout(function () {
				self.isActive = 0;
				self.showOne = true;
				self.showTwo = false;
				self.showThree = false;
			},3000);
			
		}
	}
})

var newvue = new Vue({
	el: '#youNameId',

})

</script>

</html>
