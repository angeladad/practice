<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>无标题文档</title>
<style>
*{margin:0;padding:0;}
li{list-style:none;}
#box{width:600px;height:460px;border:4px solid #000;margin:100px auto;position:relative;overflow:hidden;}
a{color:black;text-decoration:none;}
#box .pic img{width:600px;height:460px;float:left;}
#box .pic li{width:600px;height:460px;float:left;}

#box .pic{width:3000px;display:inline-block;position:relative;z-index:-1;left:0;}
#box ol{position:absolute;right:0 ;bottom:0;}
#box ol li{width:20px;height:20px;border:1px solid #000;background:#ccc;text-align:center;line-height:20px;float:left;opacity:0.6;}
#jt_left{width:10px;height:20px;background:#A9FF00;padding:5px;position:absolute;left:0;top:200px;opacity:0.4;}
#jt_right{width:10px;height:20px;background:#A9FF00;padding:5px;position:absolute;right:0;top:200px;opacity:0.4;}
#box ol .ac{background:#C5A123;}
</style>
<script src="move.js"></script>
<script>
window.onload=function(){
	var numBtn=document.getElementsByTagName('ol')[0].children;
	var jtLeft=document.getElementById('jt_left');
	var jtRight=document.getElementById('jt_right');	
	var oUl=document.getElementsByTagName('ul')[0];
	var aLi=oUl.children;
	var show_num=0;
	
	var li_w=getStyle(aLi[0],'width')//取li的宽度
	oUl.style.width=li_w*aLi.length+'px';
	
	for(var i=0;i<numBtn.length;i++){
		numBtn[i].index=i; // 发牌照
		numBtn[i].onclick=function(){
			for(var j=0;j<numBtn.length;j++){
				numBtn[j].className='';
			};
			this.className='ac';
			show_num=this.index;
			
			move(oUl,'left',-li_w*show_num,500)
		};
				
	};
	
	//箭头滚动
	//left
	jtLeft.onclick=function(){
		show_num--;
		if(show_num<0){show_num=4};
			move(oUl,'left',-li_w*show_num,500)
			for(var j=0;j<numBtn.length;j++){
				numBtn[j].className='';
			};
			numBtn[show_num].className='ac';
	}
	//right
	jtRight.onclick=function(){
		show_num++;
		if(show_num>numBtn.length-1){show_num=numBtn.length-1;show_num=0};
			move(oUl,'left',-li_w*show_num,500)
			for(var j=0;j<numBtn.length;j++){
				numBtn[j].className='';
			};
			numBtn[show_num].className='ac';
	}
	

}

</script>
</head>

<body>
<div id="box">
<ol>
<li class="ac"><a href="#">1</a></li>
<li><a href="#">2</a></li>
<li><a href="#">3</a></li>
<li><a href="#">4</a></li>
<li><a href="#">5</a></li>
</ol>

<ul class="pic">
<li><img src="file:///E|/js/week4/day2/img/3a037db76534f6543b65402ba2f50d53.jpg"></li>
<li><img src="file:///E|/js/week4/day2/img/1359996_3.jpg"></li>
<li><img src="file:///E|/js/week4/day2/img/3473762_2.jpg"></li>
<li><img src="file:///E|/js/week4/day2/img/20139129413542640.jpg"></li>
<li><img src="file:///E|/js/week4/day2/img/gtaiv_outdoor-younglady.jpg"></li>

</ul>
<a id="jt_left" href="#"><</a>
<a id="jt_right" href="#">></a>





</div>
</body>
</html>
