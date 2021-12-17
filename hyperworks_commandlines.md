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
