# chatbot_simbert
检索类型的微信聊天机器人/问答系统，通过API异步通信，实现在微信上交互，本项目包括模型和工程化部署一体化。用到SimBert等模型。
## 描述
各位可以根据自己的需求部署或修改：

问答库如果是任务型的，就是一个任务型聊天机器人，如果闲聊的问答库，那就是闲聊型聊天机器人；

后续也可以添加意图，用来用意图识别的匹配；也可以添加个知识图谱的API...

总之可以添加的模块很多，扩展性非常强大。

## 品尝方式（使用说明）
### 准备：
环境准备：安装requirement中的依赖包

下载模型，并放置在code/1.retrieve_match/3.simbert_match/config路径下：simbert模型：https://github.com/ZhuiyiTechnology/pretrained-models
### 启动：
- <strong>启动code/2.API_serve/KG_service.py

- <strong>启动code/3.wx_project/chat_bot.py（需要扫码登录）

开始邀请朋友和你聊天吧

如果自己有前端展示，不想通过微信来交互，可以启动QAserver，用这个API和你自己的前端做交互即可。

## 实现思路
整体工程如下，主要有三块：前端、后端、前后端交互；

- <strong>1、前端直接用微信展示，比较简单，不需要我们做什么；

- <strong>2、后端采用检索匹配模型的方式，结合粗排和精排；

- <strong>3、前后端的交互用sanic实现异步通信。




模型部分实现的主要流程如下，初始时有个问答库：

- 1、先用BM25和Bool检索把问句query和问答库做字词上的粗排，返回topN；

- 2、将query和粗排得到的topN用SimBert向量化，再将两者做consine相似度计算得到最相似的top1。
  

## 交流

微信公众号：卓拾书非卓师叔

知乎：学习学习再学习
