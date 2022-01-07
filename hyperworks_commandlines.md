# hyperworks_commandlines:


## 一、无界面调用hm命令
1.后台调用hypermesh
"C:\Program Files\Altair\2019\hm\bin\win64\hmbatch.exe" <filename-optional> -tcl tcl_filename.tcl
2.后台调用hypergraph
call "C:\Program Files\Altair\2019\hw\bin\win64\hw.exe" -b -clientconfig hwplot.dat -f getresults.mvw  –wait
call "C:\Program Files\Altair\2019\hw\bin\win64\hw.exe" -b -clientconfig hwplot.dat -tcl getcruvedata.tcl –wait

-clientconfig <client_config_filename>: Specifies the client configuration file to load.
-b: Runs the application in batch mode.  The application does not display the GUI and will exit immediately upon completion of any command line processing.
-tcl <tcl_filename>: Automatically run the specified Tcl script.


## 二、使用note可输入命令
1.page1 window2 curve1 的y轴最大值
{(max(p1w2c1.y))}

2.某个位置的y值（0.1输出间隔时36ms×10）
{(c1.y[360])} 

3.y峰值处的x索引（×输出间隔）
{indexofmax(c1.y)}

4.使用note输出值到文件示例

```hyperview
# 获得measure编号为3下最大值
{open "C:/Users/haoyuting/Desktop/test/curvefit.dat"}
Max: {max(p1w1measure3.max)}
{close}
```

![](https://mmbiz.qpic.cn/mmbiz_png/ogPM1EwKGEscMuXzLt4ABItlibPh3EbELp0ibDXaOtic60m86vEwkAgnljfX8XpGxbRwBy9cjP3uWxymfEic2Ks5pQ/640?wx_fmt=png)

```hypergraph
# 获得HIC值；p1w2c1 y轴最大值
{open "C:/Users/haoyuting/Desktop/test/curvefit.dat"}
{mynote = hic(p1w6c1.x*0.001,p1w6c1.y*1.0,15)}
HIC: {mynote[0]}
Max: {max(p1w2c1.y)}
{close}
```
```hypergraph
# 输出若干条曲线的唯一最大值
{open "C:/Users/haoyuting/Desktop/test/curvefit.dat"}
{num= (p1w1c5.y,p1w1c6.y)}
{max = {max(num)}}
befor: {num}
after: {max}
{close}
```


```hypergraph
# if语句判断值
{open "C:/Users/haoyuting/Desktop/test/curvefit.dat"}
{max = max(int(p1w1c1.y))}
Max: {max}
{if(max >40)}
high value: {max}
{elseif(max >30)}
low value: {max}
{else}
min value: {max}
{endif}
{close}
```

