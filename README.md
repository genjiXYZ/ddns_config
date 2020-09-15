## 在当前目录 python ./run.py

### 可以在openwrt 设置定时任务   


例子：0 6 * * * reboot

每天6点0分执行reboot命令。因为只设置了“分”和“时”，“日月周”都是通配符，所以只要当前时间是 6点0分，不管当前是几月几日周几都会被执行。

还是例子：0 6 * * 1,3 reboot

每周一和周三的6点0分执行reboot命令。因为“周”被设置为了1,3，逗号是将多个值分开，当条件达到其中一个值时便会执行。所以只有在周一或者是周三的6点0分才会被执行，当然，也不管当前是几月几日。

再来个例子：0 6 * 3-6 1,3 reboot

这个例子的月改为了3-6，连字符的作用是指定范围，它就是在三月至六月的每周一和每周三的6点0分执行reboot命令。其实也可以这样写0 6 * 3,4,5,6 1,3 reboot，不过这样不够简洁，推荐还是使用连字符。

斜杠例子：0 */3 * * * reboot

斜杠的作用是跳过某些特定值。你可以把它看作一个除法，当结果等于整数时才会执行。上面个例子，把时写成了*/3，星号表示任何值、/表示除法、3表示除数。那么，如果现在是1点，1/3 不是整数，就不会被执行，如果是9点，9/3 是整数，它就可以被执行。不知道我这样说大家有没有理解。（小山数学是体育老师教的）

最后一个例子：*/10 */3 * * * reboot

这个例子有两个斜杠，分别是分和时，那么不但要满足当前“分”除于10是整数，还需要满足“时”除于3是整数，比如1点10分，虽然“分”满足了条件，不过“时”并没有，只有当前时间为3点40分，这样的情况下，才会触发执行。



### */5 * * * * cd /mnt/mmcblk1p3/ddns && python ./run.py



{
  "$schema": "https://ddns.newfuture.cc/schema/v2.8.json", 
  "debug": false, 
  "dns": "dnspod", 
  "id": "dnspd ID", 
  "token": "token",
  "index4": "url:http://ip.3322.net/",
  "ipv4": [
    "liulingyue.com",
    "www.liulingyue.com"
  ],
  "proxy": null, 

  "ttl": null,
  "cache":true
}
