###圣杯模型
圣杯模型属于三栏布局，其中左右两列宽度固定，中间宽度自适应且优先展示渲染；在实际应用中，希望左右两边的高度，随中间的高度，自适应。

1. 通过类选择器，分别对center、left、right设置基础样式;其中left和right宽度固定，center宽度自适应（100%);

2. 让三个块元素都向左浮动，并利用父容器清除浮动，即通过overflow:hidden,创建BFC防止高度塌陷；

3. 此时，left排在了center后面，right排在了left后面；

4. 通过margin属性，将right向左移动left的宽度；

5. 此时，left和right压盖住了center，需要通过父级元素（padding-left，padding-right）预留出left和right的空间；

6. 再利用相对定位，使left和right回到预想位置；

html文件

	<div class="container">
		<div class="center">center
			<p>test height auto</p>
			<p>test height auto</p>
			<p>test height auto</p>
			<p>test height auto</p>
		</div>
		<div class="left">left</div>
		<div class="right">right</div>
	</div>
css文件

	.body{
		min-width: 630px;
	}
	.container{
		overflow: hidden;  /* 清除浮动 */
		padding-left: 100px;  /* 为left留出空间 */
		padding-right: 200px;  /* 为right留出空间 */
	}
	.center{
		width: 100%;
		background-color: #fff144a6;
	}
	.left{
		width: 100px;
		background-color: #33ff857a;
		margin-left: -100%; /* left排在了center后面，需要向左移动center的宽度*/
		position: relative;
		left: -100px; /* 利用相对定位，使left回到预想位置 */
	}
	.right{
		width: 200px;
		background-color: #ef348a57;
		margin-left: -200px;/* right排在了left后面，需要向左移动left的宽度*/
		position: relative;
		right: -200px;  /* 利用相对定位，使right到预想位置 */
	}
	.center, .left, .right{
		float: left;
		/* center、left、right分别增加了padding;
		  margin-bottom的负值，又回退了padding增加的值;
		  又由于容器元素overflow: hidden，将多余的部分剪裁掉，于是高度自适应了 */
		padding-bottom: 2000px; 
		margin-bottom: -2000px;
	}

###双飞翼模型
双飞翼模型属于三栏布局，其中左右两列宽度固定，中间宽度自适应且优先展示渲染。在实际应用中，希望左右两边的高度，随中间的高度，自适应。

1. 通过类选择器，分别对center-container、left、right设置基础样式，其中left和right宽度固定，center宽度自适应（100%）;
2. 让三个块元素都向左浮动，并利用父容器清除浮动，即通过overflow:hidden,创建BFC防止高度塌陷;

3. 此时，left排在了center后面，right排在了left后面;
4. 通过margin属性，将left向左移动center的宽度,right向左移动left的宽度;
5. 此时，left和right压盖住了center，需要通过center（margin-left，margin-right）预留出left和right的空间;

html文件

	<div class="container">
		<div class="center-container">
			<div class="center">center
				<p>test height auto</p>
				<p>test height auto</p>
				<p>test height auto</p>
				<p>test height auto</p>
			</div>
		</div>
		<div class="left">left</div>
		<div class="right">right</div>
	</div>

css文件

	.body{
		min-width: 630px;
	}
	.container{
		overflow: hidden;/* 清除浮动 */
	}
	.center-container{
		width: 100%;
		float: left;
	}
	.center{
		background-color: #fff144a6;
		margin-left: 100px;
		margin-right: 200px;
	}
	.left{
		width: 100px;
		background-color: #33ff857a;
		float: left;
		margin-left: -100%;/* left排在了center后面，需要向左移动center的宽度*/
	}
	.right{
		width: 200px;
		background-color: #ef348a57;
		float: left;
		margin-left: -200px;/* right排在了left后面，需要向左移动left的宽度*/
	}
	.center, .left, .right{
		/* center、left、right分别增加了padding;
		  margin-bottom的负值，又回退了padding增加的值;
		  又由于容器元素overflow: hidden，将多余的部分剪裁掉，于是高度自适应了 */
		padding-bottom: 2000px; 
		margin-bottom: -2000px;
	}

###两栏模型(一)
左边固定宽度，右边自适应的两栏布局。

- 左侧浮动，右侧形成BFC，通过“overflow: auto”实现。

html文件

	<div class="container">
		<nav class="nav">
			<div>test1</div>
			<div>test1</div>
			<div>test1</div>
			<div>test1</div>
		</nav>
		<section class="section">
			<div>test1</div>
		</section>
	</div>

css文件

	.body{
		min-width: 630px;
	}
	.container{
		overflow: hidden; /* 清除浮动 */
	}
	.nav{
		width: 200px;
		background-color: #33ff857a;
		float: left;
	}
	.section{
		background-color: #ef348a57;
		overflow: auto;
	}
	.nav, .section{
		padding-bottom: 2000px; 
		margin-bottom: -2000px;
	}

###两栏模型(二)
左边固定宽度，右边自适应的两栏布局。

- 左侧浮动，右侧宽度自适应，右侧margin让出左侧宽度。

html文件

	<div class="container">
		<nav class="nav">
			<div>test1</div>
			<div>test1</div>
			<div>test1</div>
			<div>test1</div>
		</nav>
		<section class="section">
			<div>test1</div>
		</section>
	</div>

css文件

	.body{
		min-width: 630px;
	}
	.container{
		overflow: hidden; /* 清除浮动 */
	}
	.nav{
		width: 200px;
		background-color: #33ff857a;
		float: left;
	}
	.section{
		background-color: #ef348a57;
		width: 100%; 
		margin-left: 200px;
	}
	.nav, .section{
		padding-bottom: 2000px; 
		margin-bottom: -2000px;
	}

###两栏模型(三)
左边固定宽度，右边自适应的两栏布局。

- 父元素相对位置，左侧绝对位置，右侧宽度自适应，右侧margin让出左侧宽度。

html文件

	<div class="container">
		<nav class="nav">
			<div>test1</div>
			<div>test1</div>
			<div>test1</div>
			<div>test1</div>
		</nav>
		<section class="section">
			<div>test1</div>
		</section>
	</div>

css文件

	.body{
		min-width: 630px;
	}
	.container{
		position: relative;
	}
	.nav{
		width: 200px;
		background-color: #33ff857a;
		position: absolute;
	}
	.section{
		background-color: #ef348a57;
		margin-left: 200px;
	}

###水平居中
水平居中的三种方式。

1. margin: auto；

2. 元素盒模型变为行内块，父元素使用text-align: center；

3. 定位，元素绝对定位，向右偏移50%，再反向移动元素宽度的一半；

html文件

	<div class="center1"></div>
	<div class="center2-father">
		<div class="center2"></div>
	</div>
	<div class="center3-father">
		<div class="center3"></div>
	</div>

css文件

	.body{
		min-width: 630px;
	}
	.center1{
		width: 100px;
		height: 100px;
		background-color: #33ff857a;
		margin: auto;
	}

	.center2-father{
		text-align: center;
	}
	.center2{
		width: 100px;
		height: 100px;
		background-color: #fff144a6;
		display: inline-table;
	}

	.center3-father{
		position: relative;
	}
	.center3{
		width: 100px;
		height: 100px;
		background-color: #ef348a57;
		position: absolute;
		left: 50%; /* 先向右偏移容器的一半 */
		margin-left: -50px;  /* 再反向移动元素宽度的一半 */
	}

###垂直居中
垂直居中的三种方式。

1. line-height与height相等； 

2. 父元素为table，子元素为table-cell，vertical-align: middle；

3. 定位，元素绝对定位，向下偏移50%，再反向移动元素高度的一半；

html文件

	<div class="center1-father">
		<div class="center1">center1</div>
	</div>
	<div class="center2-father">
		<div class="center2">center2</div>
	</div>
	<div class="center3-father">
		<div class="center3"></div>
	</div>

css文件

	.body{
		min-width: 630px;
	}
	.center1-father{
		width: 100px;
		height: 100px;
		background-color: #33ff857a;
		line-height: 100px;
	}

	.center2-father{
		display: table;
		margin-bottom: 50px;
	}
	.center2{
		width: 100px;
		height: 100px;
		background-color: #fff144a6;
		display: table-cell;
		vertical-align: middle;
	}

	.center3-father{
		position: relative;
	}
	.center3{
		width: 100px;
		height: 100px;
		background-color: #ef348a57;
		position: absolute;
		top: 50%;
		margin-top: -50px;
	}
