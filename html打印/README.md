1.点击CLodop_Setup_for_Win32NT.exe进行安装
2.安装完成后启动该服务
3.引入LodopFuncs.js
4.打印功能
	function printData(obj){
		var userAgent = navigator.userAgent.toLowerCase(); //取得浏览器的userAgent字符串
		if (userAgent.indexOf("trident") > -1){
			alert("请使用google或者360浏览器打印");
			return false;
		}
		else if(userAgent.indexOf('msie')>-1){ 
			var onlyChoseAlert = simpleAlert({
	           "content":"请使用Google或者360浏览器打印",
	           "buttons":{
	               "确定":function () {
	                   onlyChoseAlert.close();
	               }
	           }
	       })
			alert("请使用google或者360浏览器打印");
			return false;
		}
		else{//其它浏览器使用lodop
			var oldstr = document.body.innerHTML; 
			var headstr = '<html><head><title></title></head><body>';  
			var bodystr = '<div><table class="default-tab" style="width:100%;font-size:10px;border-collapse:collapse" border="1">';
			//bodystr += ....
			bodystr +=	"</tbody></table></div>"
			var footstr = "</body>"; 
			var LODOP = getLodop();
			LODOP.PRINT_INIT("");
			LODOP.SET_PRINT_STYLE("Alignment",3);
			LODOP.SET_PRINT_STYLE("FontSize",8);
			LODOP.SET_PRINT_PAGESIZE(3,'82mm','10mm','');
			LODOP.ADD_PRINT_HTM('5mm','2mm',"68mm","50mm",bodystr);
			//打印预览
			LODOP.PREVIEW();
			//直接打印
			LODOP.PRINT();
		}
	}