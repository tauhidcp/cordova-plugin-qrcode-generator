# cordova-plugin-qrcode-generator

this plugin can help you create qr code into html div tag and export as image file (.png/.jpeg) from android app build with cordova  

### Tested on:

- NodeJS  	      : 19.4.0
- Cordova 	      : 11.1.0
- cordova-android : 11.0 
- Java 11  

### How to use

install from github repository using this command
```
cordova plugin add https://github.com/tauhidcp/cordova-plugin-qrcode-generator.git
```
or install from npmjs package using this command 
```
cordova plugin add id.my.tauhidslab.qrcode
```

uninstall using this command
```
cordova plugin rm id.my.tauhidslab.qrcode
```

### HTML file  

first, we need to declare the container for qr code and some input tag like below  

``` 
<input id="isiqr" type="text" value="http://www.tauhidslab.my.id" style="width:90%" /><br />
<div id="qrcode" style="width:256px; height:256px; margin-top:15px;"><!--QR Code Container--></div></br>
			
<input type="button" value="Make QR" id="makeqr" ></br></br>
<input type="button" value="Download QR" id="downloadqr" ></br></br>
```

### Create QRCode 

create qr code function is implemented from jquery qrcode (http://jeromeetienne.github.com/jquery-qrcode/). example code to create qrcode from your app as you can see below  

``` 
function createQR(){
	
var qrel = document.getElementById("qrcode"); // qr code element id
var isi  = document.getElementById("isiqr").value; // qr code text value

cordova.plugins.QrGen.getQR(isi,qrel);
	
}
```

### Save QRCode to Image File (.png/.jpeg)

save to image function is implemented from html2canvas lib (http://html2canvas.hertzen.com). below example code to save qr code to image file. simply, html to canvas to image.  

```
function saveToImg(){

	var qr = document.getElementById("qrcode"); // qr code element id
	
	// create random name and store in download folder 
	var imgname = "myQR_"+Math.floor(Math.random() * 1000000000)+".jpg"; // save to png or jpg
		
	cordova.plugins.Qr2Image.getImage(onSuccess, onError, qr, imgname);
	
	function onSuccess(s){ 
		alert(s); 
	}
	
	function onError(e){ 
		alert(e); 
	
	}
	
}
```

