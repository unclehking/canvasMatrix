# canvasMatrix

模仿电影《黑客帝国》的代码雨效果，使用canvas实现。

[Demo -- 演示页面](http://unclehking.github.io/canvasMatrix/)

截图： <br />
![github](http://unclehking.github.io/canvasMatrix/screenshot.png "github")  

html:
```java  
<canvas id="c" ></canvas>
```
javascript:
```java  
	var matrix = {
		target : null,
		cTarget : null,
		txt : "た0и1极らЯйんд".split(""),
		fSize : 16,
		drops : [],
		init : function(t){
			this.target = t;
			this.cTarget = t.getContext("2d");
			this.reSize();
			setInterval(function(){
				this.draw();
			}.bind(this), 33);
			window.onresize=function(e){
				this.reSize().draw();
			}.bind(this);
		},
		draw : function(){
			this.cTarget.fillStyle = "rgba(0, 0, 0, 0.05)";
			this.cTarget.fillRect(0, 0, c.width, c.height);
			this.cTarget.fillStyle = "#0F0";
			this.cTarget.font = this.fSize + "px arial";
			this.drops.map(function(t,i,a){
				var text = this.txt[Math.floor(Math.random()*this.txt.length)];
				this.cTarget.fillText(text, i*34, t*this.fSize);
				if(t*this.fSize > c.height || Math.random() > 0.95)
					this.drops[i] = 0;
				this.drops[i]++;
			},this);
			return this;
		},
		reSize : function(){
			this.target.height = window.innerHeight;
			this.target.width  = window.innerWidth;
			var columns = this.target.width/this.fSize;
			this.drops =  new Array(parseInt(columns)).join(Math.random()*10).split("");
			return this;
		}
	};

	matrix.init(document.getElementById("c"));
```
