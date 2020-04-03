<p align="center">
    <a href="https://github.com/tangyou79/IBGP">
        <img width="200" src="./img/LOGO.png">
    </a>
</p>


# IBGP使用说明

### [I]()ntegrated [B]()ayes [G]()enomic [P]()rediction software

[简体中文](./README-zh_CN.md)&nbsp;&nbsp;|&nbsp;&nbsp;English

## Authors

> [YouTang](https://github.com/tangyou79) &nbsp;&nbsp; :e-mail:tangyou@neau.edu.cn

### 介绍



### 安装教程

- 点击上方`发行版`即可下载需要的版本

- 点击上边`附件`可下载供测试用的数据文件

- IBGP支持命令行模式和GUI模式，支持Windows、Linux和macOS

  

### 命令说明

#### 启动GUI界面

当命令中无任何参数时，会直接启动GUI界面，如：

```shell
java -jar IBGP.java
```

在Java正确安装的情况下也可以直接双击IBGP.java启动GUI界面。



#### 展示帮助信息

使用`-h`或`--help`展示帮助信息：

```bash
java -jar IBGP.java -h
usage: Options [-bin <arg>] [-bout <arg>] [-CV <arg>] [-GD <arg>] [-group
       <arg>] [-h] [-M <arg>] [-o <arg>] [-p <arg>] [-pi <arg>] [-t <arg>]
       [-times <arg>] [-v]
 -bin,--burn_in <arg>        The value of burn_in
 -bout,--burn_out <arg>      The value of burn_out
 -CV,--covariate <arg>       covariate file (optional)
 -GD,--genotype_data <arg>   genotype data file (optional)
 -group <arg>                The value of group
 -h,--help                   show help massage.
 -M,--model <arg>            BayesA, BayesB, or BayesC (default: BayesA)
 -o,--out <arg>              output file, only support .txt or .csv format
                             (required)
 -p,--phenotype <arg>        phenotype file (required)
 -pi <arg>                   The value of pi
 -t,--traits <arg>           choose trait for analysis. Multiple traits
                             could be provided with comma, like:
                             trait1,trait2,trait3
 -times <arg>                The value of times
 -v,--version
```

命令的基本格式为：

```shell
IBGP.jar --方法名 [--方法所需参数1 参数1 & --方法所需参数2 参数2 ...] --out 输出文件地址
```

例：

```shell
java -jar IBGP.jar -M BayesC -GD "E:\IBGP\genotype_data.txt" -p "E:\IBGP\phenotype.txt" -CV "E:\IBGP\myCV.txt" -bin 1 -bout 1 -pi 0.2 --out "E:\IBGP\out\BayesC.txt"
```



#### 个别参数说明：

`--out <arg>` 为必填参数，在arg中填入输出文件地址（不加<>），支持输出后缀为`.txt`和`.csv`的文件，下文不再对其说明


`--traits` 该参数用于选择运算时的表型，同GUI中的`Select traits`按钮，后接表型列名，以英文逗号分隔，如`--traits PH,EH` 或 `-t PH,EH,DTT` 

当指令没有给出`traits`参数时，系统会列出读取到的所有表型信息，此时输入需要的表型的编号即可，同样以英文逗号分隔。如：



**方法所需的参数与GUI相同，可根据GUI界面查看对应方法所需的参数**



#### BayesA

短参数`-M BayesA` 长参数`--model BayesA`

| 短参数 |    长参数     |            参数解释            |
| :----: | :-----------: | :----------------------------: |
|   GD   | genotype_data |    genotype_data文件的地址     |
|   p    |   phenotype   |      phenotype文件的地址       |
|   CV   |   covariate   |      covariate文件的地址       |
|  bin   |    burn_in    |          burn in的值           |
|  bout  |   burn_out    |          burn out的值          |
|   t    |    traits     | （可选）以英文逗号分隔的表型名 |



命令示例：

```shell
java -jar .\IBGP.jar -M BayesA -GD "E:\IBGP\genotype_data.txt" -p "E:\IBGP\phenotype.txt" -CV "E:\IBGP\myCV.txt" -o "E:\IBGP\ot\testA.txt" -bin 1 -bout 1 -t PH,EH,DTT
```



#### BayesB

短参数`-M BayesB` 长参数`--model BayesB`

| 短参数 |    长参数     |            参数解释            |
| :----: | :-----------: | :----------------------------: |
|   GD   | genotype_data |    genotype_data文件的地址     |
|   p    |   phenotype   |      phenotype文件的地址       |
|   CV   |   covariate   |      covariate文件的地址       |
|  bin   |    burn_in    |          burn in的值           |
|  bout  |   burn_out    |          burn out的值          |
|   p    |      pi       |             Pi的值             |
|   t    |    traits     | （可选）以英文逗号分隔的表型名 |



命令示例：

```shell
java -jar .\IBGP.jar -M BayesB -GD "E:\IBGP\genotype_data.txt" -p "E:\IBGP\phenotype.txt" -CV "E:\IBGP\covariate.txt" -o "E:\IBGP\out\testB.txt" -bin 1 -bout 1 -pi 0.5 -t PH,EH,DTT
```



#### Bestmethod

短参数`-M Best` 长参数`--model Best`

| 短参数 |    长参数     |            参数解释            |
| :----: | :-----------: | :----------------------------: |
|   GD   | genotype_data |    genotype_data文件的地址     |
|   p    |   phenotype   |      phenotype文件的地址       |
|   CV   |   covariate   |      covariate文件的地址       |
|  bin   |    burn_in    |          burn in的值           |
|  bout  |   burn_out    |          burn out的值          |
|   p    |      pi       |             Pi的值             |
| group  |               |           Group的值            |
| times  |               |           Times的值            |
|   t    |    traits     | （可选）以英文逗号分隔的表型名 |



命令示例：

```shell
java -jar .\IBGP.jar -M Best -GD "E:\IBGP\genotype_data.txt" -p "E:\IBGP\phenotype.txt" -CV "E:\IBGP\covariate.txt" -o "E:\IBGP\out\testBest.txt" -bin 1 -bout 1 -pi 0.5 -group 3 -times 2
```



#### BayesLASSO

短参数`-M BayesLASSO` 长参数`--model BayesLASSO`

| 短参数 |    长参数     |            参数解释            |
| :----: | :-----------: | :----------------------------: |
|   GD   | genotype_data |    genotype_data文件的地址     |
|   p    |   phenotype   |      phenotype文件的地址       |
|   t    |    Traits     | （可选）以英文逗号分隔的表型名 |



命令示例：

```shell
java -jar .\IBGP.jar -M BayesLASSO -GD "E:\IBGP\genotype_data.txt" -p "E:\IBGP\phenotype.txt" -o "E:\IBGP\out\testBL.txt"
```



#### BayesC

短参数`-M BayesC` 长参数`--model BayesC`

| 短参数 |    长参数     |            参数解释            |
| :----: | :-----------: | :----------------------------: |
|   GD   | genotype_data |    genotype_data文件的地址     |
|   p    |   phenotype   |      phenotype文件的地址       |
|   CV   |   covariate   |      covariate文件的地址       |
|  bin   |    burn_in    |          burn in的值           |
|  bout  |   burn_out    |          burn out的值          |
|   p    |      pi       |             Pi的值             |
|   t    |    traits     | （可选）以英文逗号分隔的表型名 |



命令示例：

```shell
java -jar .\IBGP.jar -M BayesC -GD "E:\IBGP\genotype_data.txt" -p "E:\IBGP\phenotype.txt" -o "E:\IBGP\out\testBL.txt"
```



#### BayesCpi

短参数`-M BayesCpi` 长参数`--model BayesCpi`

| 短参数 |    长参数     |            参数解释            |
| :----: | :-----------: | :----------------------------: |
|   GD   | genotype_data |    genotype_data文件的地址     |
|   p    |   phenotype   |      phenotype文件的地址       |
|   CV   |   covariate   |      covariate文件的地址       |
|  bin   |    burn_in    |          burn in的值           |
|  bout  |   burn_out    |          burn out的值          |
|   p    |      pi       |             Pi的值             |
|   t    |    traits     | （可选）以英文逗号分隔的表型名 |



命令示例：

```shell
java -jar .\IBGP.jar -M BayesCpi -GD "E:\IBGP\genotype_data.txt" -p "E:\IBGP\phenotype.txt" -CV "E:\IBGP\covariate.txt" -bin 1 -bout 1 -pi 0.2 -o "E:\IBGP\out\testCpi.txt"
```