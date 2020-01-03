# 智能制造系统

[前往](http://114.116.96.152:8004)

-----

## 系统简介

> 可以将车间的工作流程应用控制中心的功能一一展现出来，方便人们不用进入车间便可以了解车间的具体结构， 方便管理者对车间的架构进行调控，更利于车间的管理
![The Vue Instance Lifecycle](/images/springBootVUE.png)
## 工艺流程

>功能包括BOM管理，工艺流程版本和路径管理，工序管理，资源管理，工序绘制关联关系等。将原来表格文档化的内容管理转为可视化管理。 将逻辑性较强的关系数据转为可视化数据管理，结构清晰，层次分明。计划应用在生产单位的工艺流程管理系统中。
![The Vue Instance Lifecycle](/images/technologyTree.png)
## 生产计划

### 生产计划

生产计划是对应生产系统所做的一系列计划，可以在不同的生产计划上做多个版本的修改，可以实时的进行报工，对其完成的数量也可以进行实时的监控
![The Vue Instance Lifecycle](/images/plan.png)

### 计划版本

生产计划版本管理
1)	添加/编辑：录入数据包括部门【数据来自部门管理】、产品【数据来自产品管理】、开始时间、结束时间。
2)	版本复制：复制直接版本，主要用于版本修改。
3)	发布版本：将确定版本发布，计划数据推送到“部门管理”里的“任务分配管理”中，用于做为部门任务分配管理的基础数据，以及报工数据的统计依据。
![The Vue Instance Lifecycle](/images/planVersion.png)

### 版本明细

版本明细
统计数据为：交付需求、交付需求累计、生产计划、完成数量、累计完成数量、需要结转量【生产量与需求生产量有出入，需要制定下一个生产计划完成此数据，现程序为新建生产计划时，选择需要承接某一个生产计划】、报工统计【用于显示除上述数据外的其他数据信息。现程序中没有此模块】。此模块中的数据，现程序部分数据为人工输入，以后报工完成后，数据来源应该来自报工数据。
![The Vue Instance Lifecycle](/images/planVersionDetail.png)
## 质量管理

工序和检验需求是属于一一对应的关系，检验需求内涵检验需求类别的属性，检验需求对应对个检验项，检验项包含检验标准，检验类别和检验单位属性 工序下包含多条工序任务，可以根据工序对应的检验需求和检验项对应生成多个检验任务和检验项，将检验需求作为一个模板去使用。在执行检验任务时，真正检测时又分为实测和观感两种检测方式
## 工艺树
![The Vue Instance Lifecycle](/images/technologyTree.png)
该树是由产品—工件—工艺—工序组成，打开树可以看见产品------工序树中的每一个节点的显示，仅作为显示， 只有最后一层的工序才可以进行点击。
## 质量检查
   ### 任务管理
![The Vue Instance Lifecycle](/images/checkTaskTree.png)
该任务树是由产品，工件，工艺，工序和工序任务组成，每一层都可以点击，完整的诠释了产品------工序任务的每一个节点，可以直观的看出该树的架构和每个节点的名称，但是只有最后一个节点可进行点击。
创建检验任务—派发检验任务—执行检验任务—生成该检验任务的结论并进行查看
### 检验任务
![The Vue Instance Lifecycle](/images/checkTaskList.png)
派发的检验任务规则：
1.	检验任务必须有检验人
2.	计划的开始时间和结束时间不能为空且：当前时间<计划开始时间<计划结束时间
3.	检验任务下的检验项的检验人不能为空，这样派发后才会有具体人执行
符合以上条件后，点击右侧的派发按钮，该检验任务就派发到指定的检验员

### 检验数据反馈
![The Vue Instance Lifecycle](/images/checkTaskTree.png)
数据录入分为两大类：
实测类
进入检验任务列表—检验项列表，选择自己检验的检验项，进入数据录入界面，
实测类在添加数据的同时，直接生成检验结果（判定结论是根据上下公差和实际值）得出的。
观感类
添加观感描述，根据观感测量人为判断是否合格

### 检验数据管理
![The Vue Instance Lifecycle](/images/lookCheckTask.png)
该树总共分为7层，由产品，工件，工艺，工序，工序任务，检验任务和检验项组成，点击每一个节点都会该节点所对应的的列表数据，可以用于领导观看进度和总体架构。
### 统计图分析
![The Vue Instance Lifecycle](/images/statistics.png)

## 数据字典

### 单位管理
![The Vue Instance Lifecycle](/images/unit.png)

### 检验标准
![The Vue Instance Lifecycle](/images/standard.png)

### 检验类型
![The Vue Instance Lifecycle](/images/type.png)

## 控制中心

本系统可以将制造系统的软硬件结合起来使用，实现真正的智能制造，内涵看板，站位任务等多个模块 可以给操作人员提供更多的便捷
![The Vue Instance Lifecycle](/images/controlcenter.png)
## 物料管理

物料管理是指将新入库的物料分配货架进行管理，以及该物料的合并入库，分批出库等操作将物料分别放入不同的位置 在该过程中也可以对该物料进行出线和上报异常。
1.已有实际物料展示界面
主要是展示库存和在制品信息，物料种类，数量，位置
2.物料需求信息展示界面
以人物师徒展示每道工序需要展示需要物料的种类、数量、时间.
3.物料需求满足界面
以物料所在部门/区域的物料管理角色，展示该部门/区域物料的需求信息。然后对需求进行匹配，需求与已有库存进行匹配，并给出物料需求满足状态，具体物料/满足多少/缺货等信息
4.物料配送任务界面
依据物料需求的满足信息，依据物料的原始地和目的地，生成对应的物料配送任务界面，主要包括物料的种类数量，运转箱、原始地、目的地。
5.任务反馈的物料信息录入界面
在任务开始加工前，通过配送过来的物料编码，录入到任务的消耗物料列表中。

### 物料类型
![The Vue Instance Lifecycle](/images/materialType.png)

### 物料管理
![The Vue Instance Lifecycle](/images/materialInfo.png)

### 产品-任务
![The Vue Instance Lifecycle](/images/productTask.png)

### 站位任务
![The Vue Instance Lifecycle](/images/siteTask.png)


## 工艺流程
功能包括BOM管理，工艺流程版本和路径管理，工序管理，资源管理，工序绘制关联关系等。将原来表格文档化的内容管理转为可视化管理。 将逻辑性较强的关系数据转为可视化数据管理，结构清晰，层次分明。计划应用在生产单位的工艺流程管理系统中。
![The Vue Instance Lifecycle](/images/technology.png)

## 关于本书

本书不是技术书籍，它很短，它就是想尽量用最简单的方式给小白讲清楚区块链的 “最少必要知识”。

本书内容保存在 [github](https://github.com/xiaolai/blockchainlittlebook.com) 上，点击右上角那个小猫的图标，就可以转至该项目的仓库。

本书完全开源，没有任何协议，你可以任意修改，任意发布 —— 只不过，希望你注意以下两点：

> * 保留原文出处，加上原站链接：https://blockchainlittlebook.com
> * 如若做出了修改，最好在保留原文的情况下，加上醒目的修改标注。

欢迎各种语言的翻译 —— 请提交 pull request。请将翻译文件放置到相应的目录之中，文件仍然命名为 README.md，比如

> /en/README.md
>
> /jp/README.md

**你甚至可以用它做自己的网站！** —— 自己先去买一个域名就好。

在你注册好自己的 github 账户之后，你就可以 Fork 当前这个项目为自己的仓库：

![](images/fork1.png)

Fork 完成之后，点开 Settings

![](images/fork2.png)

往下拉，拉到 GitHub Pages 单元，Source 中选择 ```master branch```：

![](images/fork3.png)

而后在 Custom Domain 中填写你自己的域名（你可以在 [name.com](https://www.name.com/) 上或者[阿里云](https://www.net.cn)上购买域名）：

![](images/fork4.png)

你需要在域名服务商的页面中，为自己的域名添加以下 4 条 A 记录和 1 条 CNAME 记录：

> A 记录：
>
> * 185.199.108.153
> * 185.199.109.153
> * 185.199.110.153
> * 185.199.111.153
>
> CNAME
>
> host: www
>
> Anser: *your-github-username*.github.io

我的设置如下：

![](images/custom-domain.png)

大功告成！几分钟之后，你就可以看到你自己的域名已经生效了，若是你身边有人想要了解区块链，那么你就可以给他属于你自己的链接了。如果需要修改内容，直接在 GitHub 页面里编辑即可……

注意：原仓库会经常更新，所以，你也要将你的 Fork 保持更新：

```bash
git clone https://github.com/gitbasictutorial/blockchainlittlebook.com
cd blockchainlittlebook.com
git remote add upstream https://github.com/xiaolai/blockchainlittlebook.com
git pull upstream master
git push -u origin master
```

## 关于作者

李笑来，投资人，终生成长者。[http://lixiaolai.com](http://lixiaolai.com) · [xiaolai@github](https://github.com/xiaolai)

### 出版书籍

> * TOEFL 核心词汇 21 天突破
> * [TOEFL 高分作文](http://lixiaolai.com/#/twe185/)
> * [把时间当作朋友](http://lixiaolai.com/#/befriending-time/)
> * 通往财富自由之路
> * 韭菜的自我修养（[中文](http://lixiaolai.com/#/the-self-cultivation-of-leeks/cn/) · [English](http://lixiaolai.com/#/the-self-cultivation-of-leeks/en/)）
> * [自学是门手艺](http://lixiaolai.com/#/the-craft-of-selfteaching/)
> * [定投改变命运（第三版）](https://onregularinvesting.com)

### 其它

> * [我也有话要说](http://lixiaolai.com/#/i-have-a-say/)
> * [人人都能用英语](http://lixiaolai.com/#/everyone-can-use-english/)
> * [挤挤都会有的 —— 写给女生的性高潮指南](http://lixiaolai.com/#/ji/)
> * INBlockchain 开源投资原则 ([中文](http://lixiaolai.com/#/INB-principles/cn/) · [English](http://lixiaolai.com/#/INB-principles/en/))
> * [Bitcoin 白皮书（中英对照）](http://lixiaolai.com/#/bitcoin-whitepaper-cn-en-translation/Bitcoin-Whitepaper-EN-CN.html)
> * [区块链小白书](https://blockchainlittlebook.com)
