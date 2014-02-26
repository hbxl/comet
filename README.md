1.flush,ob_flush,ob_end_flush,ob_end_clean区别

flush：将不在缓冲区或者被释放的内容刷到浏览器

ob_flush:释放缓冲区的内容

ob_end_clean,ob_end_flush:关闭缓冲区

2.php缓冲区开启及大小配置

php.ini中搜索outpu_buffering,可更改其值关闭开启缓冲区，一般都会默认打开且大小为4096B

3.ini_set(”output_buffering”,”0″)无法设置缓冲区大小为0，因为脚本一开始时缓冲设置就已载入，ini_set已无法更改其值。

4.所以在写comet时仅flush是不够的，仅flush数据仍然会先送到缓冲区等到数据完成或者缓冲区满了发到浏览器，解决方案是：

a.ob_end_clean();

  flush();
  
b.ob_end_flush();

  flush();
  
c.ob_flush();

  flush();
  
参考资料：http://www.jb51.net/article/16215.htm
