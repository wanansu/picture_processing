1. 程序主函数为project，categener和paragener为用于生成所需参数的脚本。其他函数为主程序所调用。
2. paragener读取存放于mask文件夹下的模板图片，生成模板的特征向量组“gist2.mat”保存在data文件
夹下，运行project时自动读取进行匹配。
3. categener脚本读取data文件夹下的category.xlsx来导入商品种类、保质期和过期期限，生成系统变量
“category.mat”供主程序运行时调用，实际场景下把商品信息写入category.xlsx，并且运行一次categener.m
即可实现对其的识别。
4. 程序依赖于相对路径，整个文件夹可任意放置。
5. GIST文件夹来自GIST算法原作者，未作修改，运行project前请将其添加到MATLAB系统路径。
6. 待识别图片应为RGB类型，放在pic文件夹下，修改project.m中tilt_corrc()中图片名即可处理该图片。
7. 识别流程为先运行project.m处理条码图片（程序可以区别图片中包含的是条码还是生产日期，但是如果图
片同时包含两者，则只会识别条码），接下来直到下一次识别到条码为止，都认为识别到的生产日期属于前一
次识别到的条码对应的商品，此间识别得到的信息会累积式地写到data文件夹下的“统计表.xlsx”中，一整次
结余统计完成后直接取走该文件即可，注意下次统计时不能保留上次统计的“统计表.xlsx”，也不需要由用户新建
“统计表.xlsx”，程序运行一次后会自己生成。
8. data文件夹下的following.mat是程序运行中产生的参数，不能删去，否则会丢失上一次识别的商品种类信
息。
