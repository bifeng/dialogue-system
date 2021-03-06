refer:<br>[语音识别和NLP在语音交互中的实践](https://blog.csdn.net/dQCFKyQDXYm3F8rB0/article/details/79933707) [pdf](https://doc.huodongjia.com/detail-6953.html)

#### 语音技术

![系统架构](https://github.com/bifeng/dialogue-system/raw/master/image/voice_system_architect.png)

难点：

第一，前端-唤醒、回声消除、声源定位。小爱同学唤醒还是比较容易，但经常会发生误唤醒，可能还没有说“小爱同学”，它就唤醒了，甚至你说什么小白同学、小赖同学，也可能会唤醒。

所以唤醒技术本身就很复杂，小爱同学现在已经训练有接近 1 年时间了，但做得还不是很好，其实用户还想要更多的唤醒词来去叫醒它。

当一个唤醒词我们花了 1 年的时间训练，怎么样把一个唤醒词的技术更加通用化、能让用户自定义自己的唤醒词就好了。例如我的小孩叫丹丹，我们可以直接跟音箱说，“丹丹你好”，用户有这样的需求，但我们的技术现在没有做到。

第二，语音识别-噪音环境下的识别、中英文混杂、不同人声（老人/小孩）、方言。语音识别有噪音环境，声音混杂，不同的人有不同的方言，我们集成了国内所有语音技术的提供商，但现在没有任何一家有特别好的用户体验。

第三，语音合成-实体词、中英文混杂。两年前，语音合成在整个中国一年产出的人才不超过 20 个，所以现在做语音合成的人才，在语音交互的场景里炙手可热。

语音合成里面有非常多的问题，一个是合成实体词。比如用户自己说，这个“618”要促销了，就是我们自己知道“618”什么意思，但机器看不到“618”，它不知道你说的是 6、1、8 还是 618（六百一十八），它看到的字是一样的，但是它念出来——如果说六百一十八要促销——大家就会觉得很奇异，因为它背后有很多的知识。

那么，通过知识怎么样去融合进来，做语音合成，这又很复杂，包括中英文混杂，用户情感怎么样处理，这点上其实小冰做得比较好，它的合成声音带着情感，这个技术其实目前看也是最好的。

#### 自然语言理解

**首先要有一个清晰的产品定义。**

自然语言理解的背后我们认为这个 query 应该给什么样的用户结果，使得这个产品给用户的体验最好。

当用户将一个 query 发给小爱同学的时候，它有 4 种应答方式：

1.我们有一个叫内置垂域，比如查天气、定闹钟都是小爱同学内部自己的团队来去定义的。

2.我们会把这个能力开放给设备开发者，包括我们自己的设备，譬如在手机上说打开手电筒，就是设备所独有的，它不是一种通用能力。譬如说一个电视，连接 HDMIE，我们相信小爱同学自己是做不了的，所以我们就把这个能力开放出来，交给设备开发者，由他们自己去定义。

3.开放平台。大家对这个行业了解一下就应该知道，它本身是一个操作系统，它上面可以有无数多的 APP，很多的开发者愿意在小爱同学上面去开发 APP，譬如像开发菜谱，开发成语接龙、开发冒险世界这种语音交互类的这种游戏，在亚马逊的内容已经有接近 3-4 万了，在小爱同学上面现在有 100-200 种。

4.小爱的训练计划。这个我们看到大家用的最多的，第一个就是逗小孩或者逗家人，比如世界上最美的是谁啊？直接把你老婆的名字念出来，世界上谁聪明啊？把自己小孩念出来……针对自定义的去说出自己希望说的话，也就是把高度定制化的能力交给用户。

用户可以自己训练小爱，小爱刚开始运作起来也是挺傻的，但你如果有耐心去训练它，让它能够跟你作伴，这其实是整个小爱同学的一个产品。

**其次，就是垂域的深度优化。**

垂域理解就是每一个垂域用的算法、方法都是不一样的，譬如说北京明天天气怎么样？北京明天晴转多云。单说这句话其实是一个天气类的，但你直接前头加入一下“翻译”两个字，它就变成了一个翻译类的。

![语义理解](https://github.com/bifeng/dialogue-system/raw/master/image/vertical_nlu.png)

下一个例子就是韩磊《南山南》，本身韩磊没唱过《南山南》，所以就把它**纠错**成张磊。为什么我们知道韩磊没有唱过《南山南》呢？因为它本身是带有知识库的，所以要做好这个领域的话，首先不光要知道相应的**词表**，必须得需要相应的**知识**，知道用户想找音乐，然后到知识库里去判断它到底是歌手还是歌名，看看有没有这个歌手和歌名，然后找到相应的歌给用户。

最后一个是用户闲聊的需求，例如用户问“天猫精灵怎么样”，这种 query 是很难回答的，我们也不知道怎么回答，我们这一块其实就是**通过有多少人工就有多少智能的方式**。把这种 query 能运营好，但我们也希望尽可能通过算法能让这个人工的方式更智能，所以后面可以稍微期待一下。

语义的垂域理解，这块还是挺复杂的，每一个垂域自己的知识库和领域都是很复杂的。要理解这种用户的复杂查询的话，一定要对后台的知识库，甚至是用户有深度的理解，所以针对视频这一块，非常简单列了一下，我们有 25 个相应的知识字段去构建知识库，只有这样的话，才能把用户复杂的查询构建好。

![视频领域](https://github.com/bifeng/dialogue-system/raw/master/image/video_domain_word_table.png)

##### 词表-有限状态自动机

![词网格](https://github.com/bifeng/dialogue-system/raw/master/image/word_grid.png)

词网格是一个比较基础的自然语言理解模块，在分词和词道用的非常多。

平时用户说打开卧室的灯，但是由于口音问题，或者是距离的问题，就是 AI 在识别的时候，它经常会“打开卧室壁灯”，或者“大开卧室的灯”，识别出不同可能性出来。这是语音识别的结果给 NLP 的输入，基于这个输入，我们通过词网格的方式，去寻找一种最优路径，去构建出它最优的可能性。

另一个例子是，我想看功夫电影和我想看周星弛的电影《功夫》，就功夫这个词在第一个 query 里面，它其实想表达一类电影，我想看周星弛的功夫电影，它就是找这种有功夫类的电影，然后我想看周星弛的电影《功夫》，那我就是想找名字叫《功夫》的电影，这个就要根据它前面串的和后面串的一个这种相似度，在历史的统计数据里面去找到最有可能匹配的路径，这个就是词网格。

##### 文法-上下文无关文法

![CFG](https://github.com/bifeng/dialogue-system/raw/master/image/cfg.png)

刚刚我们看到的词网格的模型，它本身是基于一种有限状态思维逻辑，但是上下文无关文法是有下推的思维逻辑，它会无限的去扩展，构建出现在的模型出来。譬如，亲戚计算器，不知道大家知不知道小爱这个功能：爸爸的爸爸的爸爸叫什么？小爱同学会回答：你可以喊他高祖父。我们要解决这类问题，一定要选择相应方法。

##### 知识库搜索

???

##### 问答对匹配

???

**最后，就是全局的统一策略。**

我们就发现中控全局判别这件事越做越复杂。譬如，北京天气怎么样？翻译“北京天气怎么样”？对于天气而言的话，它就发现它前面多了两个词，它也不认识翻译，因为对于每一个垂域来讲，它都是局部的信息，很难去知道全局性的，它前面多了个翻译，自己的转换就不管了。

???

所以我们希望在中控里面，有一种全局的、多轮对话管理来保证用户的持续对话。

#### 用户行为反馈

语音交互比搜索难，搜索里面最重要的信号就是给用户的点击模型，当搜索第一天发明出来的时候，所有的搜索结果是工程师去进行的校调和排序，但只要有用户不断去用这个结果，第 1 条结果他不点开，他点了第 2 条，他一定是认为第 2 条结果肯定比第一条好，他点了第 2 条之后又点了第 3 条，那可能他对第 2 条的结果不是很满意，他觉得第 3 条可能更好。所以搜索里面通过大量的用户点击返回数据去调整搜索排序。

目前大家看到的是比较成熟的技术，用户点击反馈已经在搜索质量排序当中超过 60% 的重要性，但在语音交互这边，用户的反馈它是一种很隐式的，可能用户觉得你没听懂他，可能就会去换一种说法再问一下。

怎么样让用户反馈进入到这个模型中，帮助小爱同学去变得更聪明？实际上，目前世界上还没有看到工业界和学术界与之相关的研究成果出来。

？？？





