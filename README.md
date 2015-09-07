<html>
<head>
<title>Restaurant</title>
<link rel="stylesheet" href="css/style1.css" type="text/css" media="screen" />


<script type="application/javascript">

  function num(evt)
      {
         var charCode = (evt.which) ? evt.which : event.keyCode
         if (charCode > 31 && (charCode < 48 || charCode > 57))
            return false;

         return true;
      }
</script>

</head>
<body>

<form method = "post" action = "<?php $_SERVER['PHP_SELF']; ?>"
<div id="maincontainer">
<div id="header">Book A Table</div>
<div id="body">
<br><div class="rest-outer">
<center>
<br><h2><font color="#806517">Enter The  Following Details:</font></h2><br><br> 
<table>
<ul>
<tr><td><b><font color="#000653"><li>Restaurant Name :</li></font></td><td><input type="text" name="rname" class="input_field" value="<?php echo getvalue('rname'); ?>" /> <font color="#000653"></font></b></td></tr>
<tr><td><b><font color="#000653"><li>Number of People :</li></font></td><td><SELECT NAME="people"  class="input_field" >
<OPTION VALUE="1">1 People</OPTION>
 <OPTION VALUE="2">2 People</OPTION>
<OPTION VALUE="3">3 People</OPTION>
<OPTION VALUE="4">4 People</OPTION>
<OPTION VALUE="5">5 People and more</OPTION>
</SELECT></b></td><tr>
<tr><td><b><font color="#000653"><li>Date:</li></font></td><td><input type="date" name="date" class="input_field" min ="2015-09-08" width = 50px value="<?php echo getvalue('date'); ?>" /></b></td><tr>
<tr><td><b><font color="#000653"><li>Timing:</li></font></td><td><SELECT NAME="time" class="input_field" >
<OPTION VALUE="10A">10 AM </OPTION>
<OPTION VALUE="11A">11 AM </OPTION>
<OPTION VALUE="12P">12 PM </OPTION>
<OPTION VALUE="1P">1 PM </OPTION>
<OPTION VALUE="2P">2 PM</OPTION>
<OPTION VALUE="3P">3 PM</OPTION>
<OPTION VALUE="4P">4 PM</OPTION>
<OPTION VALUE="5P">5 PM</OPTION>
<OPTION VALUE="6P">6 PM</OPTION>
<OPTION VALUE="7P">7 PM</OPTION>
<OPTION VALUE="8P">8 PM</OPTION>
<OPTION VALUE="9P">9 PM</OPTION>
<OPTION VALUE="10p">10 PM </OPTION>
</select>
<b></td><td></br><br>
<tr><td><b><font color="#000653"><li>Mobile:</li></font></td><td><input type="mob" class="input_field" onkeypress="return num(event)" maxlength="11" name="mob" value="<?php echo getvalue('mob'); ?>" /><b><font color="#000653"></font></b></td><td>
</table>
</ul>
</center>
<div class="submit-margin">
<br><br><input type="submit" value="submit" name="submit"></br></div>
</form>


<?php

if(isset($_POST['submit']))
{ 

$rname=$_POST['rname'];
$people=$_POST['people'];
$date=$_POST['date'];
$time= $_POST['time'];
$mob=$_POST['mob'];

$host="localhost";
$user="root";
$pass="";
$db="rest";


$connection = mysql_connect($host,$user,$pass) or die("unable to connect");

mysql_select_db($db) or die("unable to connect");

mysql_select_db("$db", $connection);




if(($rname == NULL) || ($people == NULL) ||($date == NULL) ||($time == NULL) ||($mob == NULL) )
{
?><center><FONT COLOR="red"><?php echo"field cannot remain empty";?></FONT></center><?php

}
else
{

	?><center><FONT COLOR="red"><?php echo"Thanks for details";?></FONT></center><?php
	mysql_query("INSERT INTO booking(rname,people,date,time,mob) VALUES('$rname','$people','$date','$time','$mob')");

}
}
function getvalue($val)
{
if(isset($_POST[$val]))
{
return $_POST[$val];
}
else
{
return "";
}
}


?>
<br><br><center><a href="login.php">LOGOUT</a></center>
            </center>


</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>
</div>

</body>
</html>
