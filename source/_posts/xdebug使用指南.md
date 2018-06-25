---
title: xdebug使用指南
date: 2016-06-17 10:45:27
categories:
 - PHP
 - xdebug
tags:
 - xdebug
---
查看xdebug官方手册，对手册里出现的一些调用方法进行翻译及记录。
```php
xdebug_call_class();    //调用的类名
xdebug_call_file();     //调用的文件的绝对地址
xdebug_call_line();     //调用方法在文件的行数
xdebug_call_function(); //调用的方法名
xdebug_disable();       //禁止显示错误的跟踪栈信息
xdebug_enable();        //激活显示错误的跟踪栈信息
xdebug_start_error_collection();    //错误收集开始，并记录在缓冲区
xdebug_stop_error_collection();     //错误停止收集
xdebug_get_collected_errors();      //获取收集的所有错误，返回数组，配合以上俩函数使用
xdebug_get_headers();   //获取所有由PHP设置的header信息，比如header(),setcookie()函数设置的信息。返回数组
xdebug_is_enabled();    //返回跟踪是否开启，即配置项xdebug.default_enable的值
xdebug_memory_usage();  //返回当前内存使用值
xdebug_peak_memory_usage();         //返回程序运行期间内存使用的峰值
xdebug_time_index();    //返回脚本开始到现在使用的时间，单位为秒
xdebug_debug_zval();    
xdebug_debug_zval_stdout();         //返回一个变量的标准输出信息，包括类型，值，引用次数等。
xdebug_dump_superglobals();         //显示所有全局变量
xdebug_get_declared_vars();         //返回当前范围内定义的变量集合
xdebug_get_function_stack();        //函数执行步骤
xdebug_start_function_monitor();    //开始收集监控方法,参数以方法名为元素的数组
xdebug_stop_function_monitor();     //停止收集监控方法
xdebug_get_monitored_functions();   //获取收集的监控方法
xdebug_print_function_stack();      //用自定义的message替换系统默认,并报错 参数为string, 可加option(XDEBUG_STACK_NO_DESC)取消警告
xdebug_start_trace();               //开启调试缓存 如已配置php.ini文件 则已自动缓存
xdebug_stop_trace();
xdebug_get_tracefile_name();        //获取trace文件位置
xdebug_start_code_coverage();       //开始收集代码覆盖信息 其中,键(1已执行，-1未执行，-2没有可执行代码)
xdebug_code_coverage_started();     //判断是否有活跃的代码覆盖率方法
xdebug_stop_code_coverage();        //停止收集代码覆盖信息 option(true默认删除覆盖信息 false不删除)
xdebug_get_code_coverage();         //获取代码覆盖率信息
```
其它重要的功能点还有 `PHP` 脚本性能测试 `xdebug_get_profiler_filename()` 及 `xdebug_break()` 断点调试。
需要借助第三方工具实现, 具体配置及使用方法，还是需要看[官方手册](https://xdebug.org/docs/);

下面是我的php.ini文件的xdebug配置
```ini
zend_extension=xdebug.so
display_errors=on
xdebug.profiler_enable=on
xdebug.trace_output_dir = "/var/log/xdebug_trace_log"
xdebug.profiler_output_dir = "/var/log/xdebug_profiler_log"
xdebug.auto_trace = On ;开启自动跟踪
xdebug.show_exception_trace = On ;开启异常跟踪
xdebug.remote_autostart = Off ;开启远程调试自动启动
xdebug.remote_enable = On ;开启远程调试
xdebug.remote_handler=dbgp ;用于zend studio远程调试的应用层通信协议
xdebug.remote_host=127.0.0.1 ;允许连接的zend studio的IP地址
xdebug.remote_port=9000 ;反向连接zend studio使用的端口
xdebug.collect_vars = On ;收集变量
xdebug.collect_return = On ;收集返回值
xdebug.collect_params = 4 ;收集参数
xdebug.max_nesting_level = 10000 ;如果设得太小,函数中有递归调用自身次数太多时会报超过最大嵌套数错
xdebug.cli_color = 1 ;CLI模式显示颜色
xdebug.dump_globals = On
xdebug.show_local_vars = On
xdebug.dump.superglobals = On
xdebug.dump.SERVER = REQUEST_URI
```
