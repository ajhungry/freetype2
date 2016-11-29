# freetype2
My personal branch of the freetype2 modify by version 2.6.2. 
Source code:https://sourceforge.net/projects/freetype/files/freetype2/2.6.2/

官方发布的freetype2.6.2版本加载位图时增加了是否递归死循环的检测判断，但是带来了新问题。该bug在2.6.3版本中依然存在，但是在2.6.4版本中得到了解决。因此，直接参考2.6.4的源码更新2.6.2版本的源码，经过试验，可以解决问题。
主要修改发生在两处：
1.freetype-2.6.2\freetype-2.6.2\src\truetype\ttgload.c  的1644-1669行代码 
2.第一处修改后的代码添加了ft_list_get_node_at函数，在freetype-2.6.2\freetype-2.6.2\src\truetype\ttgload.c 中的load_truetype_glyph函数（定义在1401行）前添加ft_list_get_node_at定义和实现：（可参考freetype-2.6.4\src\truetype\ttgload.c 1382-1402行代码）
