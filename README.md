12-11
=====
4.html
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>哈工大旧物交易系统</title>
    <link href="images0235/style.css" rel="Stylesheet" type="text/css" />
</head>
<body>
<table border="1" width = "1400px">
    <!-- 第一行 LOGO -->
	<tr> <td colspan="2"><center><img src="image/logo.gif"/> </td> </tr>
	<!-- 第二行 目录 -->
	<tr colpan="2">
		<table border="1" width="100%">
		<td>
		<td><a href="foo.html" target="_self"><strong>首页 </strong> </a></td>
		<td><a href="2.html" target="_self"><strong>图书</strong></a></td>
		<td><a href="3.html" target="_self"><strong>生活杂物</strong></a></td>
		<td><a href="4.html" target="_self"><strong>免费专区</strong></a></td>
		<td><a href="5.html" target="_self"><strong>灌水区</strong></a></td>
		<td><a href="6.html" target="_self"><strong>登录</strong></a></td>
		<td><a href="7.html" target="_self"><strong>注册</strong></a></td>
		</table>
	<p>这是免费专区</p>
	</tr>	
	<!-- 第六行 版权声明 -->
    <tr>
        <td colspan="2" class="td_6">
            郑重声明：本站不负责交易的具体细节，之提供交易信息的平台，若交易过程中出现任何问题，本站相关工作人员概不负责！
        </td>
    </tr>
</table>	
</body>
</html>

===============
login.php
<! DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transtitional//EN"
"http://www.w3.org/TR/xhtml/DTD/xhtml1-transtitional.dtd">
<html xmlns = "http://www.w3.org/1999/xhtml" xml:lang="en" lang = "en">
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset= utf-8">
	<title> this is another page</title>
	</head>	
	<body>
		<?php
			$username = $_POST['txt_username'];
			$password = $_POST['txt_pwd'];
			if ($abc = mysql_connect('localhost','root',''))
			mysql_select_db('mytest');
			$query = "select count(*) as isexist from info_of_user where (username = '$username' and password ='$password')";
			$r = mysql_query($query);
			$row = mysql_fetch_array($r);
			$is_exist = $row['isexist'];
			if ($is_exist < 1) print('<p> <a href = "http://localhost/soft_0.1/login.html" > 用户名不存在或密码错误，请返回登录 </a> </p>');
			else {
				$query = "select * from info_of_user where username = '$username' and password ='$password'";
				$r = mysql_query($query);
				$row = mysql_fetch_array($r);
				session_start();
				$_SESSION['name'] = $row['username'];
				$_SESSION['num'] = 1;
				print('<p><a href = "http://localhost/soft_0.1/foo.php"> 登录成功，返回首页</a></p>');
			}
			$_SESSION['name'] = $username;
			
		?>
	</body>
</html>

===================
register.html
<! DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transtitional//EN"
"http://www.w3.org/TR/xhtml/DTD/xhtml1-transtitional.dtd">
<html xmlns = "http://www.w3.org/1999/xhtml" xml:lang="en" lang = "en">
<head>
	 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>注册</title>
    <link href="images7/style.css" rel="Stylesheet" type="text/css" />
</head>
<body class="bodycss">
    <form action="register.php" method="post">
    <table class="tablecss" cellspacing="0" cellpadding="0">
        <tr>
            <td colspan="3" class="td_top">会员注册</td>
        </tr>
        
         <tr>
            <td class="td_center1"> 用户名</td>
            <td class="td_center2"> <input type="text" name="txt_username"  class="txt1"/> </td>
            <td class="td_center3"><div class="span1"><img src="images7/reg1.gif" class="img1"/>不超过12个英文字符</div></td>
        </tr>
       <tr>
            <td class="td_center1"> Email地址</td>
            <td class="td_center2"> <input type="text" name="txt_email" class="txt1" /> </td>
            <td class="td_center3"><div class="span1"><img src="images7/reg1.gif" class="img1"/>请输入邮箱</div></td>
        </tr> <tr>
            <td class="td_center1"> 密码</td>
            <td class="td_center2"> <input type="password" name="txt_pwd"  class="txt1"/> </td>
            <td class="td_center3"><div class="span1"><img src="images7/reg1.gif" class="img1"/></div></td>
        </tr> <tr>
            <td class="td_center1"> 确认密码</td>
            <td class="td_center2"> <input type="password" name="sure_txt_pwd"  class="txt1"/> </td>
            <td class="td_center3"><div class="span1"><img src="images7/reg1.gif" class="img1"/></div></td>
        </tr>
		</tr> <tr>
            <td class="td_center1"> 联系电话 </td>
            <td class="td_center2"> <input type="text" name="txt_iphone"  class="txt1"/> </td>
            <td class="td_center3"><div class="span1"><img src="images7/reg1.gif" class="img1"/></div></td>
        </tr> <tr>
            <td class="td_center1"> QQ </td>
            <td class="td_center2"> <input type="text" name="txt_qq"  class="txt1"/> </td>
            <td class="td_center3"><div class="span1"><img src="images7/reg1.gif" class="img1"/></div></td>
        </tr>
        <tr>
            <td colspan="3" align="center">
               <!-- <input type="reset" name="btn_reset" class="btn_1" value="重置" />-->
                <input type="submit" name="btn_submit" class="btn_1" value="注册" />
            </td>
        </tr>
        <tr>
            <td colspan="3" class="td_bottom"></td>
        </tr>
    </table>
    </form>
</body>
</html>

===================
register.php
<! DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transtitional//EN"
"http://www.w3.org/TR/xhtml/DTD/xhtml1-transtitional.dtd">
<html xmlns = "http://www.w3.org/1999/xhtml" xml:lang="en" lang = "en">
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset= utf-8">
	<title> this is another page</title>
	</head>	
	<body>
		<?php
			$txt_username = $_POST['txt_username'];
			$txt_email = $_POST['txt_email'];
			$txt_pwd= $_POST['txt_pwd'];
			$sure_txt_pwd = $_POST['sure_txt_pwd'];
			$txt_iphone = $_POST['txt_iphone'];
			$txt_qq = $_POST['txt_qq'];
			if ($abc = mysql_connect('localhost','root',''))
			mysql_select_db('mytest');
			$query = "select count(*) as same_user from info_of_user where (username ='$txt_username')";
			$r = mysql_query($query);
			$row = mysql_fetch_array($r);
			$is_same_user = $row['same_user'];
			if ($is_same_user > 0) print('<p><a href = http://localhost/soft_0.1/register.html> 用户名已存在，请重新注册 </a></p>');
			else if ($txt_pwd === $sure_txt_pwd){
				$query = "insert into info_of_user(username,password,email,ipone,qq) values('$txt_username','$txt_pwd','$txt_email','$txt_iphone','$txt_qq')";
				mysql_query($query);
				print("<p> 注册成功 </p>");
				}
			else print('<p><a href = http://localhost/soft_0.1/register.html> 两次密码输入不匹配，请重新注册 </a></p>');
			mysql_close();
		?>
		<a href="foo.php"> 返回首页 </a>
	</body>
</html>
=====================
state.html

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
"http://www.w3.org/TR/html4/loose.dtd">
<html>

<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>哈工大旧物交易系统</title>
    <link href="images0235/style.css" rel="Stylesheet" type="text/css" />
</head>

<style type="text/css">
<!--
a.col_cp:hover,a.col_cp:link,a.col_cp:visited {color:#7677ca;}
#cp{width:760px;color:#7677ca;text-align:center;height:20px;padding-top:2px;font-size:12px;font-family:arial;}
-->
</style>
<body>
<table width="760" border="0" align="center" cellpadding="0" cellspacing="0">
  <tr>
    
  </tr>
</table>
<br><center>
<div class="dwall">
<div class="dwleft"><div class="padL_1"><br></div><br>
  <div class="padL_3">
    
	<span class="t_bg_yellow" style="font-family:arial;color:black;font-size:36px;">免责声明</span><br>
    
  <center>
  </center>
</div>
<div class="dwri_bule">  
  <table border="0" cellpadding="0" cellspacing="0">

  <tr> 

    <td valign="top">
	 
      <p>哈工大旧物交易系统</p>
	  <hr />
      <ul>
	  
	  <pre>
		<li><abbr title="哈工大旧物交易系统">本站</abbr>提醒您：<abbr title="哈工大旧物交易系统">本站</abbr>概不负责交易的具体细节，只提供交易信息的平台，若交易过程中出现任何问题，<abbr title="哈工大旧物交易系统">本站</abbr>相关工作人员概不负责！</li>
        <li><abbr title="哈工大旧物交易系统">本站</abbr>提醒您：除<abbr title="哈工大旧物交易系统">本站</abbr>注明之服务条款外，其他一切因使用<abbr title="哈工大旧物交易系统">本站</abbr>而可能遭致的意外、疏忽、侵权及其造成的损失本站对其概不负责，亦不承担任何法律责任。</li>
        <li><abbr title="哈工大旧物交易系统">本站</abbr>提醒您：<abbr title="哈工大旧物交易系统">本站</abbr>尊重并保护所有使用百度用户的个人隐私权，您注册的用户名、电子邮件地址等个人资料，非经您亲自许可或根据相关法律、法规的强制性规定，<abbr title="哈工大旧物交易系统">本站</abbr>不会主动地泄露给第三方。</li>
		<li><abbr title="哈工大旧物交易系统">本站</abbr>提醒您：您在设置为公开信息时所涉及的内容将不被认为是您的个人隐私资料。</li>
        <li><abbr title="哈工大旧物交易系统">本站</abbr>提醒您：您在<abbr title="哈工大旧物交易系统">本站</abbr>发表的任何观点信息，仅代表用户个人意见，不代表本站观点。</li>
		<li><abbr title="哈工大旧物交易系统">本站</abbr>提醒您：在使用<abbr title="哈工大旧物交易系统">本系统</abbr>前，请您务必仔细阅读并透彻理解本声明。您可以选择不使用<abbr title="哈工大旧物交易系统">本系统</abbr>，但如果您使用<abbr title="哈工大旧物交易系统">本系统</abbr>，您的使用行为将被视为对本声明全部内容的认可。</li>
		<li><abbr title="哈工大旧物交易系统">本站</abbr>提醒您：使用<abbr title="哈工大旧物交易系统">本系统</abbr>用户，自觉遵守中华人民共和国法律条文。任何违法违规行为，使用者承担一切后果。</li>
      </pre></ul></td>
  </tr>
</table>
  </div>
  <div id="cp" style="clear:both ">&copy;2013&nbsp;CS-Partner&nbsp;<a href="foo.php"  class="col_cp">旧物交易系统</a></div>
</div>
</center

</body>
</html>

===================
your.html
<! DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transtitional//EN"
"http://www.w3.org/TR/xhtml/DTD/xhtml1-transtitional.dtd">
<html xmlns = "http://www.w3.org/1999/xhtml" xml:lang="en" lang = "en">
<head>
<meta http-equiv="Content-Type" content="text/html; charset= utf-8">
<title> logn in </title>
	<style type = "text/css">
		body{
			margin :0px.0px,0px,0px;
			background:#9F9;
		}
		#rightcontent{
			float:right;
			width:85%;
			height:50%;
			background:#fff;
			border-right:2px solid #000;
			border-bottom:2px solid #000;
			margin-right:15px;
			padding-bottom:20px;
		}
		p,h1,pre{
			margin:0px,30px,10px,30px;
		}
		h1{
			font-size:14px;
			padding-top:10px;
		}
		#leftcontent p{
			font-size:14px;
			margin-right:0px;
		}
	</style>
</head>
<body>
<div id = "rightcontent">
	<p> This is message</p>
</div>	
<div id  = "leftcontent">
	<h1>menu</h1>
	<p><a href = "log_in.html">log in</a></p>
	<p><a href = "things.html">thing</a></p>
	<p><a href = "adout_us.html">adout us</a></p>
</div>
</body>
</html>

========================
book.php
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>哈工大旧物交易系统-图书</title>
    <link href="images0235/style.css" rel="Stylesheet" type="text/css" />
</head>
<body  bgcolor = "#83C296">
<table  border="1" width = "1400px">
    <!-- 第一行 LOGO -->
	<tr> <td colspan="2"><center><img src="image/logo.gif"/> </td> </tr>
	<tr>
	<?php
		session_start();
		$this_num = $_SESSION['num'];
		if ($this_num == 1) 
		{
			$name = $_SESSION['name'];
			print("<p> 欢迎您，$name  ");
			print('<a href = "http://localhost/soft_0.1/self/public.php"> 发布信息 </a>');
			print('<a href = "http://localhost/soft_0.1/exit.php" >            退出系统 </a> </p>');
		}
	?>
	</tr>
	<!-- 第二行 目录 -->
	<tr colpan="2">
		<table border="1" width="100%">
		<hr>
		<td bgcolor ="#9D9807"><a href="foo.php" target="_self"><strong><center>首页</center></strong> </a></td>
		<td bgcolor ="#9D9807"><a href="book.php" target="_self"><strong><center>图书</center></strong></a></form></td> 
		<td bgcolor ="#9D9807"><a href="life.php" target="_self"><strong><center>生活杂物</center></strong></a></td>
		<td bgcolor ="#9D9807"><a href="free.php" target="_self"><strong><center>免费专区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="talk.html" target="_self"><strong><center>需求区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="login.html" target="_self"><strong><center>登录</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="register.html" target="_self"><strong><center>注册</strong></strong></a></td>
		</table>
	</tr>
	<?php
	$abc = mysql_connect('localhost','root','');
	mysql_select_db('mytest');
	mysql_query("set names utf8");
	?>
	<table width = "100%" height = "300" frame = "border" rules = "all" border = "3">
<?php
	$query = "select count(*) as this_num from info_of_thing where kind = '1';";
	$r = mysql_query($query);
	$row = mysql_fetch_array($r);
	$this_num = $row['this_num'];
	$query = "select * from info_of_thing where kind = '1';";
	$r = mysql_query($query);
	while  ($this_num > 0){
?>
	<tr>
		<?php
			for ($i=1;$i<=4;$i++){
			if ($this_num > 0)
			{
		?>
			
				<?php
					$row = mysql_fetch_array($r);
					{
						$this_id = $row['id'];
						$this_name = $row['name'];
						$this_adress = 'self/'.$row["pic"];
						print("<td><p>$this_name</p> ");
						//print("<p>$this_name</p></td>")；
						?>
						<img src= '<?php echo $this_adress?>' width = "200" height = "200"/>
						<?php 
						$this_num = $this_num-1;
						print("<p><a href='current.php?id={$this_id}'>查看物品</p></a></td>");
					}
				?>
			
		<?php
			}
			}
		?>
	</tr>
<?php
	}
?>
</table>
	<!-- 第六行 版权声明 -->
	<pre>
	<br/><br/><br/><br/>
    <tr>
        <td "center" colspan="2" class="td_6">
				郑重声明：本站不负责交易的具体细节，之提供交易信息的平台，若交易过程中出现任何问题，本站相关工作人员概不负责！
        </td>
	</tr>
	<br/><br/><br/><br/><br/>
	<div id="cp" style="clear:both ">                                                              © 2013&nbsp;CS-Partner&nbsp;<a href="state.html" class="col_cp">旧物交易系统</a>
	</div>
	<center>
    </pre>
</table>	
</body>
</html>

==================
current.php
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>哈工大旧物交易系统-免费</title>
    <link href="images0235/style.css" rel="Stylesheet" type="text/css" />
</head>
<body>
<?php
	$this_id = $_GET['id'];
	$abc = mysql_connect('localhost','root','');
	mysql_select_db('mytest');
	mysql_query("set names utf8");
	$query =  "select * from info_of_thing where id = '$this_id'";
	$abc = mysql_query($query);
	while ($r = mysql_fetch_array($abc))
	{
		$this_adress = 'self/'.$r["pic"];
	?>
		<img src= '<?php echo $this_adress?>' width = "390" height = "390"/>
				
	<?php
	}
	//print $_GET['id'];
?>
</body>
</html>

=================
exit.php
<! DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transtitional//EN"
"http://www.w3.org/TR/xhtml/DTD/xhtml1-transtitional.dtd">
<html xmlns = "http://www.w3.org/1999/xhtml" xml:lang="en" lang = "en">
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset= utf-8">
	<title> this is another page</title>
	</head>	
	<body>
		<?php
			session_start();
			$_SESSION['num'] = 0;
			print('<p> <a href = "http://localhost/soft_0.1/foo.php" > 退出成功，返回首页 </a> </p>');
		?>
	</body>
</html>

=================
foo.php
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>哈工大旧物交易系统</title>
    <link href="images0235/style.css" rel="Stylesheet" type="text/css" />
</head>
<body bgcolor = "#83C296">
<table  border = "1" width = "1400px">
    <!-- 第一行 LOGO -->
	<tr> <td colspan="2"><center><img src="image/logo.gif"/> </td> </tr>
	<tr>
	<?php
		session_start();
		 !$this_num = $_SESSION['num'];
		if ($this_num == 1) 
		{
			$name = $_SESSION['name'];
			print("<p> 欢迎您，$name  ");
			print('<a href = "http://localhost/soft_0.1/self/public.php"> 发布信息 </a>');
			print('<a href = "http://localhost/soft_0.1/exit.php" >退出系统 </a> </p>');
		}
	?>
	</tr>
	<!-- 第二行 目录 -->
	<tr colpan="2">
		<table border = "1" width="100%">
		<hr>
		<td bgcolor ="#9D9807"><a href="foo.php" target="_self"><strong><center>首页</center></strong> </a></td>
		<td bgcolor ="#9D9807"><a href="book.php" target="_self"><strong><center>图书</center></strong></a></form></td> 
		<td bgcolor ="#9D9807"><a href="life.php" target="_self"><strong><center>生活杂物</center></strong></a></td>
		<td bgcolor ="#9D9807"><a href="free.php" target="_self"><strong><center>免费专区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="talk.html" target="_self"><strong><center>需求区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="login.html" target="_self"><strong><center>登录</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="register.html" target="_self"><strong><center>注册</strong></strong></a></td>
		</table>
	</tr>
	<!-- 第六行 版权声明 -->
	<pre>
	<br/><br/><br/><br/>
    <tr>
        <td "center" colspan="2" class="td_6">
				郑重声明：本站不负责交易的具体细节，之提供交易信息的平台，若交易过程中出现任何问题，本站相关工作人员概不负责！
        </td>
	</tr>
	<br/><br/><br/><br/><br/>
	<div id="cp" style="clear:both ">                                                              © 2013&nbsp;CS-Partner&nbsp;<a href="state.html" class="col_cp">旧物交易系统</a>
	</div>
	<center>
    </pre>
</table>	
</body>
</html>

==============
free.php
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>哈工大旧物交易系统-免费</title>
    <link href="images0235/style.css" rel="Stylesheet" type="text/css" />
</head>
<body  bgcolor = "#83C296">
<table  border="1" width = "1400px">
    <!-- 第一行 LOGO -->
	<tr> <td colspan="2"><center><img src="image/logo.gif"/> </td> </tr>
	<tr>
	<?php
		session_start();
		$this_num = $_SESSION['num'];
		if ($this_num == 1) 
		{
			$name = $_SESSION['name'];
			print("<p> 欢迎您，$name  ");
			print('<a href = "http://localhost/soft_0.1/self/public.php"> 发布信息 </a>');
			print('<a href = "http://localhost/soft_0.1/exit.php" >            退出系统 </a> </p>');
		}
	?>
	</tr>
	<!-- 第二行 目录 -->
	<tr colpan="2">
		<table border="1" width="100%">
		<hr>
		<td bgcolor ="#9D9807"><a href="foo.php" target="_self"><strong><center>首页</center></strong> </a></td>
		<td bgcolor ="#9D9807"><a href="book.php" target="_self"><strong><center>图书</center></strong></a></form></td> 
		<td bgcolor ="#9D9807"><a href="life.php" target="_self"><strong><center>生活杂物</center></strong></a></td>
		<td bgcolor ="#9D9807"><a href="free.php" target="_self"><strong><center>免费专区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="talk.html" target="_self"><strong><center>需求区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="login.html" target="_self"><strong><center>登录</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="register.html" target="_self"><strong><center>注册</strong></strong></a></td>
		</table>
	</tr>
		<?php
	$abc = mysql_connect('localhost','root','');
	mysql_select_db('mytest');
	?>
	<table width = "100%" height = "300" frame = "border" rules = "all" border = "3">
<?php
	$query = "select count(*) as this_num from info_of_thing where kind = '2';";
	$r = mysql_query($query);
	$row = mysql_fetch_array($r);
	$this_num = $row['this_num'];
	$query = "select * from info_of_thing where kind = '2';";
	$r = mysql_query($query);
	while  ($this_num > 0){
?>
	<tr>
		<?php
			for ($i=1;$i<=3;$i++){
			if ($this_num > 0)
			{
		?>
			
				<?php
					$row = mysql_fetch_array($r);
					{
						$this_id = $row['id'];
						$this_name = $row['name'];
						$this_adress = 'self/'.$row["pic"];
						print("<td><p>$this_name</p> ");
						//print("<p>$this_name</p></td>")；
						?>
						<img src= '<?php echo $this_adress?>' width = "200" height = "200"/>
						<?php 
						$this_num = $this_num-1;
						print("<p><a href='current.php?id={$this_id}'>查看物品</p></a></td>");
					}
				?>
			
		<?php
			}
			}
		?>
	</tr>
<?php
	}
?>
</table>
	<!-- 第六行 版权声明 -->
	<pre>
	<br/><br/><br/><br/>
    <tr>
        <td "center" colspan="2" class="td_6">
				郑重声明：本站不负责交易的具体细节，之提供交易信息的平台，若交易过程中出现任何问题，本站相关工作人员概不负责！
        </td>
	</tr>
	<br/><br/><br/><br/><br/>
	<div id="cp" style="clear:both ">                                                              © 2013&nbsp;CS-Partner&nbsp;<a href="state.html" class="col_cp">旧物交易系统</a>
	</div>
	<center>
    </pre>
</table>	
</body>
</html>

=============
life.php
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>哈工大旧物交易系统-生活杂物</title>
    <link href="images0235/style.css" rel="Stylesheet" type="text/css" />
</head>
<body  bgcolor = "#83C296">
<table  border="1" width = "1400px">
    <!-- 第一行 LOGO -->
	<tr> <td colspan="2"><center><img src="image/logo.gif"/> </td> </tr>
	<tr>
	<?php
		session_start();
		$this_num = $_SESSION['num'];
		if ($this_num == 1) 
		{
			$name = $_SESSION['name'];
			print("<p> 欢迎您，$name  ");
			print('<a href = "http://localhost/soft_0.1/self/public.php"> 发布信息 </a>');
			print('<a href = "http://localhost/soft_0.1/exit.php" >            退出系统 </a> </p>');
		}
	?>
	</tr>
	<!-- 第二行 目录 -->
	<tr colpan="2">
		<table border="1" width="100%">
		<hr>
		<td bgcolor ="#9D9807"><a href="foo.php" target="_self"><strong><center>首页</center></strong> </a></td>
		<td bgcolor ="#9D9807"><a href="book.php" target="_self"><strong><center>图书</center></strong></a></form></td> 
		<td bgcolor ="#9D9807"><a href="life.php" target="_self"><strong><center>生活杂物</center></strong></a></td>
		<td bgcolor ="#9D9807"><a href="free.php" target="_self"><strong><center>免费专区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="talk.html" target="_self"><strong><center>需求区</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="login.html" target="_self"><strong><center>登录</strong></strong></a></td>
		<td bgcolor ="#9D9807"><a href="register.html" target="_self"><strong><center>注册</strong></strong></a></td>
		</table>
	</tr>
		<?php
	$abc = mysql_connect('localhost','root','');
	mysql_select_db('mytest');
	?>
	<table width = "100%" height = "300" frame = "border" rules = "all" border = "3">
<?php
	$query = "select count(*) as this_num from info_of_thing where kind = '3';";
	$r = mysql_query($query);
	$row = mysql_fetch_array($r);
	$this_num = $row['this_num'];
	$query = "select * from info_of_thing where kind = '3';";
	$r = mysql_query($query);
	while  ($this_num > 0){
?>
	<tr>
		<?php
			for ($i=1;$i<=3;$i++){
			if ($this_num > 0)
			{
		?>
			
				<?php
					$row = mysql_fetch_array($r);
					{
						$this_id = $row['id'];
						$this_name = $row['name'];
						$this_adress = 'self/'.$row["pic"];
						print("<td><p>$this_name</p> ");
						//print("<p>$this_name</p></td>")；
						?>
						<img src= '<?php echo $this_adress?>' width = "200" height = "200"/>
						<?php 
						$this_num = $this_num-1;
						print("<p><a href='current.php?id={$this_id}'>查看物品</p></a></td>");
					}
				?>
			
		<?php
			}
			}
		?>
	</tr>
<?php
	}
?>
</table>
	<!-- 第六行 版权声明 -->
	<pre>
	<br/><br/><br/><br/>
    <tr>
        <td "center" colspan="2" class="td_6">
				郑重声明：本站不负责交易的具体细节，之提供交易信息的平台，若交易过程中出现任何问题，本站相关工作人员概不负责！
        </td>
	</tr>
	<br/><br/><br/><br/><br/>
	<div id="cp" style="clear:both ">                                                              © 2013&nbsp;CS-Partner&nbsp;<a href="state.html" class="col_cp">旧物交易系统</a>
	</div>
	<center>
    </pre>
</table>	
</body>
</html>

=================
login.html
<! DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transtitional//EN"
"http://www.w3.org/TR/xhtml/DTD/xhtml1-transtitional.dtd">
<html xmlns = "http://www.w3.org/1999/xhtml" xml:lang="en" lang = "en">
<head>
	 <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>注册</title>
    <link href="images7/style.css" rel="Stylesheet" type="text/css" />
</head>
<body class="bodycss">
    <form action="login.php" method="post">
    <table class="tablecss" cellspacing="0" cellpadding="0">
        <tr>
            <td colspan="3" class="td_top">用户登录</td>
        </tr>
        
         <tr>
            <td class="td_center1"> 用户名</td>
            <td class="td_center2"> <input type="text" name="txt_username"  class="txt1"/> </td>
        </tr>
		<tr>
            <td class="td_center1"> 密码</td>
            <td class="td_center2"> <input type="password" name="txt_pwd"  class="txt1"/> </td>
        </tr>
        <tr>
            <td colspan="3" align="center">
               <!-- <input type="reset" name="btn_reset" class="btn_1" value="重置" />-->
                <input type="submit" name="btn_submit" class="btn_1" value="登录" />
            </td>
        </tr>
        <tr>
            <td colspan="3" class="td_bottom"></td>
        </tr>
    </table>
    </form>
</body>
</html>
