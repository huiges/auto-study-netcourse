# auto-study-netcourse
电子科技大学网教平台自动刷课时、自动完成作业脚本  

## 0、原理及如何使用
 0）总的来说，就是分析页面Dom结构，并用代码实现自动化。  
 1）刷课时原理：获取页面上的切换课件按钮以及翻页按钮，定时检测是否已完成并点击。  
 2）作业提交原理：：先进行`初考`，默认选中每题的第一个选项并交卷，有考试记录后，`查看考卷`即可`获取试题及其答案`，此时写入`浏览器缓存`，`重考`时即可读取缓存比对试题及答案，选中正确的选项。  
 3）网课平台学习界面，各模块嵌套了很多层iframe，且跨域，要实现自动刷课时及完成作业，必须先关闭浏览器同源策略，详细步骤请参照下列说明。  
 4）GitHub说明页地址：https://swzyt.github.io/auto-study-netcourse  
 5）GitHub源代码地址：https://github.com/swzyt/auto-study-netcourse  
 6）码云源代码地址：https://gitee.com/suwei.me/auto-study-netcourse

## 1、关闭浏览器同源策略
 0）参考操作：https://www.cnblogs.com/cshi/p/5660039.html  
 1）亲测 google chrome 和 新版 Microsoft Edge 可用，其他浏览器没试过，大家自行尝试。  
　　一般来讲，`Chromium系`的浏览器应该均可使用，IE系的，未测试。  
 2）此步骤必须完成，且保证无误，才可进行后续步骤，否则会报跨域的错误，以致不能自动刷课。  

## 2、刷课时
 0）登录网课平台后，选择一门课程，点击开始学习，选择一个课件，进入课件播放页。  
 1）鼠标右键 检查/审查元素 或 F12，打开浏览器调试器。  
 2）将脚本 `0-课件-自动学习.js` 的代码复制到Console栏内，按下回车，即可自动刷课。  

## 3、作业提交
 0）登录网课平台后，选择一门课程，选择一项作业，点击`开始考试`进入考试界面，并打开浏览器调试器。  
 1）试题答案选项在同一行  
　　1.1）将脚本 `1.1-作业-初考-选项在一行.js` 的代码复制到Console栏内  
　　　　按下回车，即可完成初次考试，以便下一步获取答案。  
　　　　完成后，关闭考试界面，再次打开同一作业，点击`查看考卷`。  
　　1.2）将脚本 `2.1-作业-获取答案-选项在一行.js` 的代码复制到Console栏内  
　　　　按下回车，即可获取到试题答案，并缓存，以便下一步自动考试。  
　　　　完成后，关闭考试界面，再次打开同一作业，点击`重考`。  
　　1.3）将脚本 `3.1-作业-自动完成-选项在一行.js` 的代码复制到Console栏内  
　　　　按下回车，即可自动考试，交卷即可。  
 2）试题答案选项在多行  
　　2.1）将脚本 `1.2-作业-初考-选项在多行.js` 的代码复制到Console栏内  
　　　　按下回车，即可完成初次考试，以便下一步获取答案。  
　　　　完成后，关闭考试界面，再次打开同一作业，点击`查看考卷`。  
　　2.2）将脚本 `2.2-作业-获取答案-选项在多行.js` 的代码复制到Console栏内  
　　　　按下回车，即可获取到试题答案，并缓存，以便下一步自动考试。  
　　　　完成后，关闭考试界面，再次打开同一作业，点击`重考`。  
　　2.3）将脚本 `3.2-作业-自动完成-选项在多行.js` 的代码复制到Console栏内  
　　　　按下回车，即可自动考试，交卷即可。  

## 4、已知问题
 0）非专业前端，代码写的丑，不喜勿喷。  
 1）目前测试，所有课程的课件都能自动刷课。  
 2）作业提交  
　　2.1）数学类的课程暂时用不了，因为其试题和答案内容涉及到图形，脚本无法自动找到正确答案并完成作业  
　　2.2）可能会出现少数试题无法找到正确答案的情况，如有碰到，自行找到正确答案后选中即可。  
　　2.3）部分作业的试题答案选项，为3项的用不了，目前适配的都是为4项的，3项的需单独适配，有兴趣的同学可自行尝试修改代码。难度不大，基本上只需要修改代码中`获取答案选项的数组索引值`就行。  
　　2.4）不保证所有除数学外的课程均能使用。  
 3）平台代码调整我会不定时更新，我毕业了就不管了。😃  
 4）对于代码实现有更好建议的欢迎联系我。  

## 5、侵权问题
 0）本脚本纯粹为方便自己，开源是为了方便大家，也未以此牟利，仅因为每次开课了一直盯着刷非常的累！  
 1）本脚本不涉及到对网站的破解，不支持秒刷课时，秒做题；仅支持按照步骤一步步完成；  
　　市面上有很多收费代刷的平台或个人，可能是有对网站进行破解的程序。  

## 6、收费问题
 0）开源就不是为了收费的，刚写完脚本的时候，也有过授权收费的想法，但很快就放弃了，没有那个精力和时间去做代刷业务。  
 1）如果有的同学用这个脚本去做代刷业务的，赚了钱记得分点我，😃 。。。  
 2）有受到本脚本帮助的同学，可以考虑给我发个小红包鼓励下，😃 ，收款码先放为敬。。

## 7、捐赠
 >请作者吃个肉夹馍 :)  

[![](pic/alipay.jpg)](pic/alipay.jpg "支付宝")[![](pic/wechat.jpg)](pic/wechat.jpg "微信")
