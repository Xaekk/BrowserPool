# BrowserPool
A very good BrowserPool, try to use it & you will fall in love with it.<br/>
一个非常好用的浏览器池。<br/>
<br/>
基于Python的自动管理浏览器池，黑盒使用，不需要关心内部实现，只需 申请-使用-释放-关闭 即可。<br/>
基于Selenium-Chrome，具有内存优化、浏览器数量控制、最小化/有/无头显示、懒加载、图片有/无加载、软关闭、输出调试等功能，源码力求简单清晰，方便修改与使用。<br/>
<br/>
使用方法：<br/>
from browser_pool import browser_pool #直接引用浏览器池<br/>
browser = browser_pool.acquire() #向浏览器池申请浏览器<br/>
browser.get(URL) #使用浏览器等操作<br/>
browser.release() #使用后释放浏览器<br/>
browser_pool.close() #程序结束后，关闭浏览器池<br/>
<br/>
参数配置：<br/>
browser_amount：浏览器总数量，如果数量小于1，意味着不限量<br/>
minimize：是否最小化显示<br/>
memory_rate：内存使用率，参数范围0~100，即期望使用率乘以100<br/>
lazy_load：是否懒加载，默认为是，即随用随加载浏览器，反之预先加载全部期望使用浏览器数量<br/>
log_silence：是否调试输出当前状态<br/>
load_picture：是否载入图片<br/>
head_less：是否无头<br/>
<br/>
API：<br/>
浏览器池：<br/>
Browser_Pool.acquire：申请浏览器<br/>
Browser_Pool.clean：当前暂时不使用浏览器，清空浏览器池以节约内存<br/>
Browser_Pool.close：关闭浏览器池<br/><br/>
浏览器（继承自webdriver.Chrome）：<br/>
Browser.release：释放浏览器<br/>
Browser.destroy_by_force：强制关闭当前浏览器<br/>
Browser.browser_amount：返回当前浏览器数量，如需输出请开启调试输出<br/>
及其他父类API<br/>
