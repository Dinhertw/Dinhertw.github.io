# Dinhertw.github.io

<a href="https://dinhertw.github.io/time%20and%20date.html">時間跟日期</a><br>





<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">

    <title>time and date</title>


  
    <style >
      *{
  margin: 0;
  padding: 0;
}

body{
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #000000
}

.wrap{
 width: 900%;
 margin: 0 auto;
}

.datetime{
  color: #fff;
  font-family: "Segoe UI", sans-serif;
  width: 700%;
  padding: 150px 100px;

}


.date{
  font-size: 250%;
  font-weight: 600;
  text-align: center;
  letter-spacing: 0px;
}

.time{
  font-size: 1500%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.time span:not(:last-child){
  position: relative;
  margin: 0 6px;
  font-weight: 600;
  text-align: center;
  letter-spacing: 3%;
}

.time span:last-child{
  
  font-size: 25%;
  font-weight: 600;
  text-transform: uppercase;
  margin-top: 150px;
  padding: 0 5px;
  border-radius: 3px;
}

    </style>
  </head>
  <body onload="initClock()">

    <!--digital clock start-->
    <div class="datetime">
      <div class="date">
        <span id="dayname">Day</span>,
        <span id="month">Month</span>
        <span id="daynum">00</span>,
        <span id="year">Year</span>
      </div>
      <div class="time">
        <span id="hour">00</span>:
        <span id="minutes">00</span>:
        <span id="seconds">00</span>
        <span id="period">AM</span>
      </div>
    </div>
    <!--digital clock end-->

    <script type="text/javascript">
    function updateClock(){
      var now = new Date();
      var dname = now.getDay(),
          mo = now.getMonth(),
          dnum = now.getDate(),
          yr = now.getFullYear(),
          hou = now.getHours(),
          min = now.getMinutes(),
          sec = now.getSeconds(),
          pe = " AM";
		  
          if(hou >= 12){
            pe = " PM";
          }
          if(hou == 0){
            hou = 12;
          }
          if(hou > 12){
            hou = hou - 12;
          }

          Number.prototype.pad = function(digits){
            for(var n = this.toString(); n.length < digits; n = 0 + n);
            return n;
          }

          var months = ["January", "February", "March", "April", "May", "June", "July", "Augest", "September", "October", "November", "December"];
          var week = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
          var ids = ["dayname", "month", "daynum", "year", "hour", "minutes", "seconds", "period"];
          var values = [week[dname], months[mo], dnum.pad(2), yr, hou.pad(2), min.pad(2), sec.pad(2), pe];
          for(var i = 0; i < ids.length; i++)
          document.getElementById(ids[i]).firstChild.nodeValue = values[i];
    }

    function initClock(){
      updateClock();
      window.setInterval("updateClock()", 1);
    }
    </script>

  </body>
</html>
