## CSS的固定格式(掌握)
- ```
<style type="text/css">
        标签名称{
            属性名称：属性对应的值；
        }
   </style>
   ```
- 注意点：style标签必须写在head标签的开始标签和结束标签之间（也就是必须和title标签是兄弟关系）
          style标签中的type属性其实可以不用写，默认就是type="text/css"
          设置样式时必须按照固定的格式来设置。key:value： 其中：不能省略，分号大多数情况下也不能省略

[你是未来的幸存者吗]https://mp.weixin.qq.com/s/s5IhxV2ooX3JN_X416nidA)

## 文字相关属性(掌握)
- 规定文字样式的属性：
    格式：font-style：italic；
    取值：normal：正常的，默认就是正常的
         italic：倾斜的
    快捷键：fs + tab键:font-style:italic;
           fsn + tab键:font-style:normal;
- 规定文字粗细的属性：
    格式：font-weight:bold;
    单词取值：bold加粗 bolder比加粗还要粗 lighter细线，默认就是细线
    快捷键：fw + tab键:font-weight:;
           fwb + tab键:font-weight:bold;
           fwb + tab键r:font-weight:bolder；
    数字取值：100~900之间整百的数字
- 规定文字大小的属性：
    格式：font-size:30px;
    单位：px（像素 pixel）
    注意点：通过font-size设置大小一定要带单位，也就是一定要写px
    快捷键：fz + tab键:font-size:;
           fz30 + tab键:font-size:30px;
- 规定文字字体的属性：
    格式：font-family："楷体"；
    注意点：如果取值是中文，需要用双引号或单引号括起来
           设置的字体必须是用户电脑里已经安装好的字体
    快捷键：ff + tab键：font-famliy：；

## 字体属性补充(掌握)
- 注意：如果设置的字体不存在，那么系统会使用默认的字体来显示，在中国是显示宋体；如果设置的字体不存在，又不想使用默认的字体,可以给字体设置备选方案：
       格式：font-family:"字体1","备选方案1"，...;
        如果想给中文和英文分别单独设置字体：但凡是中文字体，里面都包含了英文；但凡是英文字体，里面都没有包含中文；也就是说中文字体可以处理英文，而英文字体不能处理中文
        如果想给界面中的英文单独设置字体，那么英文的字体必须写在中文的前面
- 补充：在企业开发中，最常见的字体有以下几个：中文：宋体、黑体、微软雅黑；英文："Times New Roman"/Arial
        还需要知道一点，不是名称是英文就一定是英文字体，因为中文字体其实都有自己的英文名称，所以是不是中文字体主要看能不能处理中文
            eg.宋体:SimSun 黑体：SimHei 微软雅黑：Microsoft YaHei

## 文字属性的简写(掌握)
- 简写格式：font：style weight size family；
        eg.font：italic bold 10px "楷体"；
- 注意点：在这种缩写格式下有些属性值可以省略 eg.style weight可以省略
          在这种缩写格式中style和weight的位置可以变换
          在这种缩写格式下有的属性值是不可以省略的 eg.size family不可以省略
          在这种缩写格式中size和family的位置不可以随意乱放，size一定要写在family前面，而且size和family一定要写在所有属性的最后

## 文本属性(掌握)
### 1、文本装饰的属性：
        格式：text-decoration:underline;
        取值：underline下划线 line-through删除线 overline上划线 none什么都没有，最常见的用途就是去掉超链接的下划线
        快捷键：td + tab键:text-decoration:none;
               tdu + tab键:text-decoration:underline;
               tdl + tab键:text-decoration:line-through;
               tdo + tab键:text-decoration:overline;
### 2、文本水平对齐的属性：
    格式：text-align：right；
    取值：left center right
    快捷键：ta + tab键：text-align：left；
           tar + tab键：text-align：right；
           tac + tab键：text-align：center；
### 3、文本缩进的属性：
    格式：text-indent：2em;
    取值：2em,其中em是单位，一个em代表缩进一个文字的宽度       
    快捷键：ti + tab键:text-indent:;
           ti2e + tab键:text-indent:2em;

## 颜色控制属性(理解)
### 1、通过color属性来修改文字颜色：
    格式：color：值；
    取值：
    英文单词：一般情况下常见的颜色都有对应的英文单词，但是英文单词能够表达的颜色是有限制的，也就是说不是所有的颜色都能够通过英文单词来表达
    rgb：格式：rgb( , , )  空格中填入的数字代表该颜色显示的亮度。每一个数字的取值是0~255,0代表不发光，255代表发光，值越大就越亮；三个数字都是0为黑色，都是255为白色，取值都相同则为灰色
         rgba：a代表透明度，取值在0~1之间
         十六进制：eg.#FFEE00 FF表示R,EE表示G,00表示B
         十六进制和十进制转换的公式：用十六进制的第一位*16 + 十六进制的第二位 = 十进制   
         eg.15 = 1*16 + 5 = 21；FF = F*16 + F == 15*16 + 15 == 255
             十六进制缩写：在CSS中只要十六进制的颜色每两位的值都是一样的，那么就可以简写为一位
                    注意点：如果当前颜色对应的两位数字不一样，那么就不能简写
                            如果两位相同的数字不是属于同一个颜色，也不能简写