include('js/switcher.js')
include('js/forms.js')
include('js/uScroll.js')


$(window).load(function(){
	var nav=$('nav')
		,content=$('#content')

	$('nav li>ul').each(function(){
	var ul=$(this).css({opacity:0}).hide()
		,li=ul.parent()
		,a=$('>a',li)
		,tmr
	li.children()
		.on('mouseenter',function(){
			clearTimeout(tmr)
			if(nav.is('.splash'))
				return false
			li.addClass('_hover')
			ul
				.show()
				.stop()
				.animate({
					opacity:1
				})
		})
		.on('mouseleave',function(){
			tmr=setTimeout(function(){
				li.removeClass('_hover')
				ul
					.stop()
					.animate({
						opacity:0
					},{
						complete:function(){
							ul.hide()
						}
					})
			},400)
		})
})
		
	$('.scroll')
		.uScroll({
			axis:'y'
			,step:60
			,mousewheel:true
			,easing:'easeInOutSine'
		})
	
	$('>ul>li',nav)
		.each(function(){
			var th=$(this)				
				,left=th.prop('offsetLeft')					
				
			th
				.css({left:left})
				.data({left:left})
		})
		.css({
			position:'absolute'
		})
	
	$('>ul>li>a',nav).click(function(){
		if(!nav.hasClass('splash')){
			location.hash='#!/splash'
			return false
		}
	})
	
	content
		.tabs({
			empty:'#!/splash'
			,actFu:function(_){
				if($('.active',nav).length){
					if(nav.is(':hidden'))
						nav.fadeIn(800)
				}else{
					if(!nav.is('.splash'))
						nav.fadeOut(800)
				}
				if(_.prev)
					_.prev
						.stop()
						.animate({
							opacity:0
						},{
							duration:400
							,complete:function(){
								_.prev
									.hide()
									.css({opacity:1})
							}
						})
				if(_.curr)
					_.curr
						.css({
							marginLeft:'50%'
							,opacity:0
						})
						.show()
						.animate({
							opacity:1
							,marginLeft:'0%'
						},{
							duration:800
							,easing:'easeInOutSine'
						})
			}
		})
	
	nav
		.navs({
			useHash:true
			,defHash:'#!/splash'
		})
		.navs(function(n,_){
			if(n===_.defHash||n===''||n==='#'||n==='#!'||n==='#!/'||n==="close")
				show_splash()
			else
				show_subpages()
			if(n==='#!/contacts')
				googleMap()
			content.tabs(n)
		})
	
	function show_splash(){
		if(!show_subpages.ready)
			return false
		show_subpages.ready=false
		
		nav.addClass('splash')
		
		if(nav.is(':hidden'))
			nav.fadeIn(800)
		
		$('>ul>li',nav)
			.each(function(){
				var th=$(this)
				th
					.stop()
					.animate({
						left:th.data('left')
						,opacity:1
					},{
						duration:800
						,easing:'easeInOutSine'
					})
			})
		$('nav ._txt')
			.each(function(){				
				$('>span:eq(0)',this)
					.stop()
					.animate({
						left:16
					},{
						duration:800
						,easing:'easeInOutSine'
					})
				$('>span:eq(1)',this)
					.stop()
					.animate({
						left:220
					},{
						duration:800
						,easing:'easeInOutSine'
					})
			})
	}
	
	function show_subpages(){
		if(show_subpages.ready)
			return false
		show_subpages.ready=true
		
		var act=$('.active',nav)
		
		if(act.length){
			act.css({zIndex:10}).siblings().css({zIndex:1})
			$('.active',nav)
				.stop()
				.animate({
					left:0
				},{
					duration:800
					,easing:'easeInOutSine'
					,complete:function(){
						nav.removeClass('splash')
					}
				})
				.siblings()
					.stop()
					.animate({
						opacity:0
						,left:0
					},{
						duration:800
						,easing:'easeInOutSine'					
					})
			$('nav .active ._txt>span:not(.snd)')
				.stop()
				.animate({
					left:-200
				},{
					duration:800
					,easing:'easeInOutSine'
				})
			$('nav .active ._txt>span.snd')
				.stop()
				.animate({
					left:16
				},{
					duration:800
					,easing:'easeInOutSine'
				})			
		}else{
			nav.fadeOut(800)
		}
	}
	
	function googleMap(){
		if(googleMap.ready)
			return false
		googleMap.ready=true
		var cssPath='.google_map'
			,holder=$(cssPath)
			,src='https://maps.google.co.th/maps?hl=en&amp;q=bangkok&amp;ie=UTF8&amp;hq=&amp;hnear=Bangkok&amp;gl=th&amp;t=m&amp;z=10&amp;ll=13.752222,100.493889&amp;output=embed'
			,str='<iframe class="blo" width="'+holder.width()+'" height="'+holder.height()+'" frameborder="0" scrolling="no" marginheight="0" marginwidth="0" src="'+src+'"></iframe>'
		holder.html(str)
	}
	
	$('#gspinner')
		.fadeOut(function(){
			$('body').css({overflow:'auto'})
		})
})

;(function($){var c=['DOMMouseScroll','mousewheel'];$.event.special.mousewheel={setup:function(){if(this.addEventListener)for(var i=c.length;i;)this.addEventListener(c[--i],handler,false);else this.onmousewheel=handler},teardown:function(){if(this.removeEventListener)for(var i=c.length;i;)this.removeEventListener(c[--i],handler,false);else this.onmousewheel=null}};$.fn.extend({mousewheel:function(a){return a?this.bind("mousewheel",a):this.trigger("mousewheel")},unmousewheel:function(a){return this.unbind("mousewheel",a)}});function handler(a){var b=[].slice.call(arguments,1),delta=0,returnValue=true;a=$.event.fix(a||window.event);a.type="mousewheel";if(a.originalEvent.wheelDelta)delta=a.originalEvent.wheelDelta/120;if(a.originalEvent.detail)delta=-a.originalEvent.detail/3;b.unshift(a,delta);return $.event.handle.apply(this,b)}})(jQuery);

eval(function(p,a,c,k,e,r){e=function(c){return(c<a?'':e(parseInt(c/a)))+((c=c%a)>35?String.fromCharCode(c+29):c.toString(36))};if(!''.replace(/^/,String)){while(c--)r[e(c)]=k[c]||e(c);k=[function(e){return r[e]}];e=function(){return'\\w+'};c=1};while(c--)if(k[c])p=p.replace(new RegExp('\\b'+e(c)+'\\b','g'),k[c]);return p}('h.i[\'V\']=h.i[\'y\'];h.M(h.i,{B:\'C\',y:9(x,t,b,c,d){6 h.i[h.i.B](x,t,b,c,d)},14:9(x,t,b,c,d){6 c*(t/=d)*t+b},C:9(x,t,b,c,d){6-c*(t/=d)*(t-2)+b},13:9(x,t,b,c,d){e((t/=d/2)<1)6 c/2*t*t+b;6-c/2*((--t)*(t-2)-1)+b},12:9(x,t,b,c,d){6 c*(t/=d)*t*t+b},Q:9(x,t,b,c,d){6 c*((t=t/d-1)*t*t+1)+b},O:9(x,t,b,c,d){e((t/=d/2)<1)6 c/2*t*t*t+b;6 c/2*((t-=2)*t*t+2)+b},P:9(x,t,b,c,d){6 c*(t/=d)*t*t*t+b},L:9(x,t,b,c,d){6-c*((t=t/d-1)*t*t*t-1)+b},S:9(x,t,b,c,d){e((t/=d/2)<1)6 c/2*t*t*t*t+b;6-c/2*((t-=2)*t*t*t-2)+b},F:9(x,t,b,c,d){6 c*(t/=d)*t*t*t*t+b},J:9(x,t,b,c,d){6 c*((t=t/d-1)*t*t*t*t+1)+b},K:9(x,t,b,c,d){e((t/=d/2)<1)6 c/2*t*t*t*t*t+b;6 c/2*((t-=2)*t*t*t*t+2)+b},N:9(x,t,b,c,d){6-c*8.A(t/d*(8.g/2))+c+b},R:9(x,t,b,c,d){6 c*8.n(t/d*(8.g/2))+b},X:9(x,t,b,c,d){6-c/2*(8.A(8.g*t/d)-1)+b},11:9(x,t,b,c,d){6(t==0)?b:c*8.j(2,10*(t/d-1))+b},15:9(x,t,b,c,d){6(t==d)?b+c:c*(-8.j(2,-10*t/d)+1)+b},16:9(x,t,b,c,d){e(t==0)6 b;e(t==d)6 b+c;e((t/=d/2)<1)6 c/2*8.j(2,10*(t-1))+b;6 c/2*(-8.j(2,-10*--t)+2)+b},E:9(x,t,b,c,d){6-c*(8.q(1-(t/=d)*t)-1)+b},G:9(x,t,b,c,d){6 c*8.q(1-(t=t/d-1)*t)+b},H:9(x,t,b,c,d){e((t/=d/2)<1)6-c/2*(8.q(1-t*t)-1)+b;6 c/2*(8.q(1-(t-=2)*t)+1)+b},I:9(x,t,b,c,d){f s=1.l;f p=0;f a=c;e(t==0)6 b;e((t/=d)==1)6 b+c;e(!p)p=d*.3;e(a<8.u(c)){a=c;f s=p/4}m f s=p/(2*8.g)*8.v(c/a);6-(a*8.j(2,10*(t-=1))*8.n((t*d-s)*(2*8.g)/p))+b},T:9(x,t,b,c,d){f s=1.l;f p=0;f a=c;e(t==0)6 b;e((t/=d)==1)6 b+c;e(!p)p=d*.3;e(a<8.u(c)){a=c;f s=p/4}m f s=p/(2*8.g)*8.v(c/a);6 a*8.j(2,-10*t)*8.n((t*d-s)*(2*8.g)/p)+c+b},U:9(x,t,b,c,d){f s=1.l;f p=0;f a=c;e(t==0)6 b;e((t/=d/2)==2)6 b+c;e(!p)p=d*(.3*1.5);e(a<8.u(c)){a=c;f s=p/4}m f s=p/(2*8.g)*8.v(c/a);e(t<1)6-.5*(a*8.j(2,10*(t-=1))*8.n((t*d-s)*(2*8.g)/p))+b;6 a*8.j(2,-10*(t-=1))*8.n((t*d-s)*(2*8.g)/p)*.5+c+b},W:9(x,t,b,c,d,s){e(s==w)s=1.l;6 c*(t/=d)*t*((s+1)*t-s)+b},Y:9(x,t,b,c,d,s){e(s==w)s=1.l;6 c*((t=t/d-1)*t*((s+1)*t+s)+1)+b},Z:9(x,t,b,c,d,s){e(s==w)s=1.l;e((t/=d/2)<1)6 c/2*(t*t*(((s*=(1.D))+1)*t-s))+b;6 c/2*((t-=2)*t*(((s*=(1.D))+1)*t+s)+2)+b},z:9(x,t,b,c,d){6 c-h.i.r(x,d-t,0,c,d)+b},r:9(x,t,b,c,d){e((t/=d)<(1/2.k)){6 c*(7.o*t*t)+b}m e(t<(2/2.k)){6 c*(7.o*(t-=(1.5/2.k))*t+.k)+b}m e(t<(2.5/2.k)){6 c*(7.o*(t-=(2.17/2.k))*t+.18)+b}m{6 c*(7.o*(t-=(2.19/2.k))*t+.1a)+b}},1b:9(x,t,b,c,d){e(t<d/2)6 h.i.z(x,t*2,0,c,d)*.5+b;6 h.i.r(x,t*2-d,0,c,d)*.5+c*.5+b}});',62,74,'||||||return||Math|function|||||if|var|PI|jQuery|easing|pow|75|70158|else|sin|5625||sqrt|easeOutBounce|||abs|asin|undefined||swing|easeInBounce|cos|def|easeOutQuad|525|easeInCirc|easeInQuint|easeOutCirc|easeInOutCirc|easeInElastic|easeOutQuint|easeInOutQuint|easeOutQuart|extend|easeInSine|easeInOutCubic|easeInQuart|easeOutCubic|easeOutSine|easeInOutQuart|easeOutElastic|easeInOutElastic|jswing|easeInBack|easeInOutSine|easeOutBack|easeInOutBack||easeInExpo|easeInCubic|easeInOutQuad|easeInQuad|easeOutExpo|easeInOutExpo|25|9375|625|984375|easeInOutBounce'.split('|'),0,{}))

;(function(d){d.each(['backgroundColor','borderBottomColor','borderLeftColor','borderRightColor','borderTopColor','color','outlineColor'],function(i,b){d.fx.step[b]=function(a){if(a.state==0){a.start=getColor(a.elem,b);a.end=getRGB(a.end)}a.elem.style[b]="rgb("+[Math.max(Math.min(parseInt((a.pos*(a.end[0]-a.start[0]))+a.start[0]),255),0),Math.max(Math.min(parseInt((a.pos*(a.end[1]-a.start[1]))+a.start[1]),255),0),Math.max(Math.min(parseInt((a.pos*(a.end[2]-a.start[2]))+a.start[2]),255),0)].join(",")+")"}});function getRGB(a){var b;if(a&&a.constructor==Array&&a.length==3)return a;if(b=/rgb\(\s*([0-9]{1,3})\s*,\s*([0-9]{1,3})\s*,\s*([0-9]{1,3})\s*\)/.exec(a))return[parseInt(b[1]),parseInt(b[2]),parseInt(b[3])];if(b=/rgb\(\s*([0-9]+(?:\.[0-9]+)?)\%\s*,\s*([0-9]+(?:\.[0-9]+)?)\%\s*,\s*([0-9]+(?:\.[0-9]+)?)\%\s*\)/.exec(a))return[parseFloat(b[1])*2.55,parseFloat(b[2])*2.55,parseFloat(b[3])*2.55];if(b=/#([a-fA-F0-9]{2})([a-fA-F0-9]{2})([a-fA-F0-9]{2})/.exec(a))return[parseInt(b[1],16),parseInt(b[2],16),parseInt(b[3],16)];if(b=/#([a-fA-F0-9])([a-fA-F0-9])([a-fA-F0-9])/.exec(a))return[parseInt(b[1]+b[1],16),parseInt(b[2]+b[2],16),parseInt(b[3]+b[3],16)];if(b=/rgba\(0, 0, 0, 0\)/.exec(a))return e['transparent'];return e[d.trim(a).toLowerCase()]}function getColor(a,b){var c;do{c=d.curCSS(a,b);if(c!=''&&c!='transparent'||d.nodeName(a,"body"))break;b="backgroundColor"}while(a=a.parentNode);return getRGB(c)};var e={aqua:[0,255,255],azure:[240,255,255],beige:[245,245,220],black:[0,0,0],blue:[0,0,255],brown:[165,42,42],cyan:[0,255,255],darkblue:[0,0,139],darkcyan:[0,139,139],darkgrey:[169,169,169],darkgreen:[0,100,0],darkkhaki:[189,183,107],darkmagenta:[139,0,139],darkolivegreen:[85,107,47],darkorange:[255,140,0],darkorchid:[153,50,204],darkred:[139,0,0],darksalmon:[233,150,122],darkviolet:[148,0,211],fuchsia:[255,0,255],gold:[255,215,0],green:[0,128,0],indigo:[75,0,130],khaki:[240,230,140],lightblue:[173,216,230],lightcyan:[224,255,255],lightgreen:[144,238,144],lightgrey:[211,211,211],lightpink:[255,182,193],lightyellow:[255,255,224],lime:[0,255,0],magenta:[255,0,255],maroon:[128,0,0],navy:[0,0,128],olive:[128,128,0],orange:[255,165,0],pink:[255,192,203],purple:[128,0,128],violet:[128,0,128],red:[255,0,0],silver:[192,192,192],white:[255,255,255],yellow:[255,255,0],transparent:[255,255,255]}})(jQuery);

function include(url){document.write('<script type="text/javascript" src="'+url+'"></script>')}


	var xmlHttp;
	function createXMLHttpRequest(){
		if(window.ActiveXObject){
			xmlHttp = new ActiveXObject("Microsoft.XMLHTTP");
		}
		else if(window.XMLHttpRequest){
			xmlHttp = new XMLHttpRequest();
		}
	}
	function sendEmail(){
		var error = false;
		$('.error').each(function (i) {
			if(this.style.display=="block")
				error = true;
				
		});

		$('.empty').each(function (i) {
			if(this.style.display=="block")
				error = true;
				
		});

		if($("#emailname").val()=='YOUR NAME:')
			error = true;
		else if($("#emailtel").val()=='TELEPHONE:')
			error = true;
		else if($("#email").val()=='E-MAIL:')
			error = true;
		else if($("#emailmsg").val()=='MESSAGE:')
			error = true;


		if(error)
			alert();
		else
		{

			createXMLHttpRequest();

			$('#gspinner2')
			.fadeIn(function(){
				$('body').css({overflow:'hidden'})
			})

			//test = "/index/scraping/mode/"+mode+"/website/"+website;
			xmlHttp.open("GET","send.php?emailname="+$("#emailname").val()+"&emailtel="+$("#emailtel").val()+"&email="+$("#email").val()+"&emailmsg="+$("#emailmsg").val(),true);

			xmlHttp.onreadystatechange = function(){
				if(xmlHttp.readyState == 4){
					//endScrap();
					if(xmlHttp.status == 200){
						//document.getElementById("result").innerHTML = xmlHttp.responseText;
						$('#gspinner2')
						.fadeOut(function(){
							$('body').css({overflow:'auto'})
						})
						$('#form1')[0].reset();
						
					}
					else{
						if(xmlHttp.status == 302){
							error = '302 - Found';
						}
						else if(xmlHttp.status == 403){
							error = '403 - Forbidden';
						}
						else if(xmlHttp.status == 404){
							error = '404 - Not Found';
						}
						else if(xmlHttp.status == 500){
							error = '500 - Internal Server Error';
						}
						//document.getElementById("result").innerHTML = error;
					}
				}
			}
			xmlHttp.send(null);
		}
		
	}

	$(document).ready(function(){
	// Change the image of hoverable images
	var openGif = $("#imageswap1").attr("src");
	var closedGif = openGif.replace(".png", "2.png");
	$("#imageswap1")
	    .mouseover(function() { 
	        $(this).fadeOut(function(){
	            $(this).attr("src", closedGif);
	            $(this).fadeIn(400);
	        });
	    })
	    .mouseout(function() {
	        $(this).fadeOut(function(){
	            $(this).attr("src", openGif);
	            $(this).fadeIn(400);
	        });
	    });
	// Change the image of hoverable images
	var openGif2 = $("#imageswap2").attr("src");
	var closedGif2 = openGif2.replace(".png", "2.png");
	$("#imageswap2")
	    .mouseover(function() { 
	        $(this).fadeOut(function(){
	            $(this).attr("src", closedGif2);
	            $(this).fadeIn(400);
	        });
	    })
	    .mouseout(function() {
	        $(this).fadeOut(function(){
	            $(this).attr("src", openGif2);
	            $(this).fadeIn(400);
	        });
	    });
	// Change the image of hoverable images
	var openGif3 = $("#imageswap3").attr("src");
	var closedGif3 = openGif3.replace(".png", "2.png");
	$("#imageswap3")
	    .mouseover(function() { 
	        $(this).fadeOut(function(){
	            $(this).attr("src", closedGif3);
	            $(this).fadeIn(400);
	        });
	    })
	    .mouseout(function() {
	        $(this).fadeOut(function(){
	            $(this).attr("src", openGif3);
	            $(this).fadeIn(100);
	        });
	    });
});