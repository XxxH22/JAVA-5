# JAVA-5
模拟学生作业处理

一、 实验目的

1. 掌握字符串String及其方法的使用

2. 掌握文件的读取/写入方法

3. 掌握异常处理结构

二、 文件处理部分要求

在某课上,学生要提交实验结果，该结果存储在一个文本文件A中。

文件A包括两部分内容：

1. 学生的基本信息；

2. 学生处理后的作业信息，该作业的业务逻辑内容是：利用已学的字符串处理知识编程完成《长恨歌》古诗的整理对齐工作，写出功能方法，实现如下功能：

1) 每7个汉字加入一个标点符号，奇数时加“，”，偶数时加“。”

2) 允许提供输入参数，统计古诗中某个字或词出现的次数

3) 输入的文本来源于文本文件B读取，把处理好的结果写入到文本文件A

4) 考虑操作中可能出现的异常，在程序中设计异常处理程序

输入：汉皇重色思倾国御宇多年求不得杨家有女初长成养在深闺人未识天生丽质难自弃一朝选在君王侧回眸一笑百媚生六宫粉黛无颜色春寒赐浴华清池温泉水滑洗凝脂侍儿扶起娇无力始是新承恩泽时云鬓花颜金步摇芙蓉帐暖度春宵春宵苦短日高起从此君王不早朝承欢侍宴无闲暇春从春游夜专夜后宫佳丽三千人三千宠爱在一身金屋妆成娇侍夜玉楼宴罢醉和春姊妹弟兄皆列士可怜光采生门户遂令天下父母心不重生男重生女骊宫高处入青云仙乐风飘处处闻缓歌慢舞凝丝竹尽日君王看不足渔阳鼙鼓动地来惊破霓裳羽衣曲九重城阙烟尘生千乘万骑西南行<未完，待续>

输出：

汉皇重色思倾国，御宇多年求不得。

杨家有女初长成，养在深闺人未识。

天生丽质难自弃，一朝选在君王侧。

回眸一笑百媚生，六宫粉黛无颜色。

春寒赐浴华清池，温泉水滑洗凝脂。

侍儿扶起娇无力，始是新承恩泽时。

云鬓花颜金步摇，芙蓉帐暖度春宵。

春宵苦短日高起，从此君王不早朝。

三、 学生类部分要求：

1. 设计学生类（可利用之前的）；

2. 采用交互式方式实例化某学生；

3. 设计程序完成上述的业务逻辑处理，并且把“古诗处理后的输出”结果存储到学生基本信息所在的文本文件A中。

四、实验流程

1.建立学生类，设计Test类
2.在学生类中创建带有修饰符private的字符串型变量name，number，team。创建变量对应的set和get函数，用来赋值与获取。利用toString来复写学生类。
3.在test类中，设立StringBuffer类ReadTxt（String path）函数，用来读取并处理文件格式。
利用FileInputStream将所定地址中的文件打开，并以字节形式进行读取。
利用InputStreamReader将上述的字节流来解码为字符型。
通过遍历将B中的字符流存入C中所建立的字符型数组中。
利用chars的数组下标和单个数组下标中的元素，通过循环将数组中的元素存入D中建立的字符串s。
在F中的循环中添加if来判断是否在字符串中添加标点与换行。
4.在test类中设计主函数main
调用ReadTxt函数。
建立while循环，利用switch和if来完成对s中出现字或词的次数查询。
在while中建立scanner类用于用户输入所需功能代码，1为查询，2为退出。
利用pattern和matcher方法，通过正则表达式来统计古诗中字或词出现的次数。
通过if与matcher方法来判断古诗中是否有输入的字或词。
通过for与if来统计同一字或词出现的次数。
初始化学生类对象。
通过scanner与学生类中set函数来实例化学生类对象。
添加try catch来对输入的值进行异常处理，并添加自定义异常与正则表达式，直到用户正确输入后，程序才会向下运行。
将学生类对象用append添加到s中，并通过writer来写入到文件中。

五、 核心代码
展示了Java如何读取文件，如何处理文件中的字符串，利用字节流来读取文件。
public static StringBuffer ReadTxt(String path) {
        StringBuffer s = new StringBuffer();
        // 读取文件内容 (输入流)
        try {
            FileInputStream out = new FileInputStream(path);
            InputStreamReader isr = new InputStreamReader(out);
            char[] chars = new char[9999999];
            int ch = 0;
            int i = 0;
            while ((ch = isr.read()) != -1) {
                chars[i] = (char) ch;
                i++;
            }
            for (int j = 0; j < i; j++) {
                s.append(chars[j]);
                if ((j + 1) % 7 == 0 && (j + 1) % 2 == 0) {
                    s.append("。" + "\n");
                }
                if ((j + 1) % 7 == 0 && (j + 1) % 2 != 0) {
                    s.append("，");
                }
            }
        } catch (Exception e) {
            System.out.println("1");
        }
        return s;
    }
六、 实验结果
![](https://github.com/XxxH22/JAVA-5/blob/main/运行截图.png)

七、实验感受
在本次实验中，我感受到了用JAVA写代码处理数据的便捷之处，同时学会了replace方法将字符串替换为空的方法，基本掌握字符串Sring的读和写入的方法，对于scanner的函数实例化更加理解。我还进一步掌握并使用Object根类的toString（）方法,应用在相关对象的信息输出中并在程序中根据输入情况做异常处理，基本掌握了文件的读取/写入方法。
