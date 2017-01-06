
t1a06-flex-servo-name.html


<html>
<head>

<meta http-equiv="Content-Security-Policy" content="default-src https://api.spark.io; style-src 'self' 'unsafe-inline'; script-src 'self' 'unsafe-inline' 'unsafe-eval' https://api.spark.io; connect-src 'self' https://api.spark.io">


<title>t1a06-flex-servo-name.html </title>

<font style="font-size:30px">



<script type="text/javascript">
<!--
var loadingmessage = 'Processing...';
function setAjax(){
   var xmlHttp;
   try{
      xmlHttp=new XMLHttpRequest(); // Firefox, Opera 8.0+, Safari
      return xmlHttp;
   }
   catch (e){
      try{
         xmlHttp=new ActiveXObject("Msxml2.XMLHTTP"); // Internet Explorer
         return xmlHttp;
      }
      catch (e){
         try{
            xmlHttp=new ActiveXObject("Microsoft.XMLHTTP");
            return xmlHttp;
         }
         catch (e){
            alert("Your browser does not support AJAX!");
            return false;
         }
     }
   }
}
function myAjax(f, url, myDivToChange) {
   var poststr = getFormValues(f);
    postData(url, poststr, myDivToChange);
}
function postData(url, parameters, myDivToChange2){
   var xmlHttp = setAjax();
   xmlHttp.onreadystatechange =  function(){
      if(xmlHttp.readyState > 0 && xmlHttp.readyState < 4){
          document.getElementById(myDivToChange2).innerHTML=loadingmessage;
      }
      if (xmlHttp.readyState == 4) {
             // this is where the magic occcurs
             
          var myJsonObject = JSON.parse(xmlHttp.responseText);
             
             
           //document.getElementById(myDivToChange2).innerHTML=xmlHttp.responseText+' data sent was '+parameters;
         
           document.getElementById(myDivToChange2).innerHTML= myJsonObject.return_value;
         
         
         
      }
   }
   xmlHttp.open("POST", url, true);
   xmlHttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
   xmlHttp.send(parameters);
}
function getFormValues(fobj){
   var str = "";
   var valueArr = null;
   var val = "";
   var cmd = "";
   for(var i = 0;i < fobj.elements.length;i++){
      switch(fobj.elements[i].type){
         case "text":
            str += fobj.elements[i].name +"=" + escape(fobj.elements[i].value) + "&";
            break;         
         case "password":
            str += fobj.elements[i].name +"=" + escape(fobj.elements[i].value) + "&";
            break;
         case "textarea":
            str += fobj.elements[i].name +"=" + escape(fobj.elements[i].value) + "&";
            break;
         case "select-one":
             str += fobj.elements[i].name +"=" + fobj.elements[i].options[fobj.elements[i].selectedIndex].value + "&";
             break;
     }
   }
   str = str.substr(0,(str.length - 1));
   return str;
}
function sendToSpark(myIn){
    document.all.myParameter.value = myIn
    document.myForm.action = 'https://api.spark.io/v1/devices/' + document.all.myDeviceId.value + '/' + document.all.myFunctionName.value
    myAjax(document.all.myCoolForm, document.myForm.action, 'myDivId')   
    
}
//--></script>







</head>

<body onload="{
   myStorage1 = localStorage.getItem('myStoredText1')
   if(myStorage1  != null){     
      document.getElementById('myToken').value = myStorage1 
    }   
    myStorage2 = localStorage.getItem('myStoredText2')
    if(myStorage2  != null){
       document.getElementById('myDeviceId').value = myStorage2      
    }
          
}">

  







<h2 align=center>Simplist Ajax Web Page for the Particle.io Photon<br> (formerly the Spark.io Core) </h2>



Device ID:<input id="myDeviceId" name="myCoreID" type=password size=50 placeholder="78dd12345678123456"> <br>
Get this from the core area when logged in<br>

<input id="myFunctionName" name="myFunction"  type=hidden size=50 value="my-main" > 

<form name="myForm" method="POST" id="myCoolForm" ><br>

<input id="myParameter" name="params" type=text  style="display:none"     size=50 placeholder="d7-send-high"> 

Access Token:<input id="myToken" name="access_token" type=password size=50 placeholder="5622ce6bba702ef6bd3456d5ed26aaa4a28d7c9"> <br>
Get this from the settings area when logged into <a href="http://spark.io">http://particle.io</a><br><br>




</form>



<input type="button" value="Store the Photon's Token and ID locally!" onClick="{
   localStorage.setItem('myStoredText2', document.all.myDeviceId.value)
   localStorage.setItem('myStoredText1', document.all.myToken.value)   
   alert('DeviceID = '+ document.all.myDeviceId.value + '\nAccess Token = ' + document.all.myToken.value + '\nHas been stored')
}">






<br><br>







<input type="button" value="d7-send-1" onClick="{
    sendToSpark('d7-send-1')
}">



<input type="button" value="d7-send-0" onClick="{
    sendToSpark('d7-send-0')
}">
<br>
   
   



<input type="button" value="a0-read" onClick="{
    sendToSpark('a0-read')
}"><br><br>


 Turn Glove Flex sensor on  
<input type="button" value="a4-flex-1" onClick="{
    sendToSpark('a4-flex-1')
}">

<input type="button" value="a4-flex-0" onClick="{
    sendToSpark('a4-flex-0')
}"><br><br>

   
   
   
   
   

<input type="button" value="a4-serv-0" onClick="{
    sendToSpark('a4-serv-0')
}">

<input type="button" value="a4-serv-45" onClick="{
    sendToSpark('a4-serv-45')
}">

<input type="button" value="a4-serv-90" onClick="{
    sendToSpark('a4-serv-90')
}">
    
Note: PWM only on A4, A5 presently<br>







<br><br>






<div width="400" height="200" name="myDivName" id="myDivId"> output here </div><br>



<input type=button id="myToVolts" value="Convert Sensor reading into Volts" onclick="{
  var myTemp = parseFloat(getElementById('myDivId').innerHTML)
  document.all.myCalc1.value = (myTemp * 3.3 / 4095).toFixed(2);
}">
: <input type=text id="myCalc1" value=0 size=5>Volts <br><br><br>











</font>
</body>
</html>
