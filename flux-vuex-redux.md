
**关于Flux,Vuex,Redux的思考**

* Flux是一种前端状态管理架构思想，专门解决软件的结构问题。
基于Flux的设计思想，出现了一批前端状态管理框架。
他们给出了一些库用于实现Flux的思想，并在Flux的基础上做了一些改进。
在这些框架里，当前最热门的莫过于Redux和Vuex了。
这里是我对Flux,Vuex,Redux的一些思考和总结:

- Flux
  - Flux数据流的顺序是:
  - View发起Action->Action传递到Dispatcher->Dispatcher将通知Store->Store的状态改变通知View进行改变

- Redux
  - Redux相对于Flux的改进：
    - 把store和Dispatcher合并,结构更加简单清晰
    - 新增state角色，代表每个时间点store对应的值，对状态的管理更加明确
  - Redux数据流的顺序是:
    - View调用store.dispatch发起Action->store接受Action(action传入reducer函数,reducer函数返回一个新的state)->通知store.subscribe订阅的重新渲染函数


- Vuex
  - Vuex是专门为Vue设计的状态管理框架,同样基于Flux架构，并吸收了Redux的优点
  - Vuex相对于Redux的不同点有:
    - 改进了Redux中的Action和Reducer函数，以mutations变化函数取代Reducer，无需switch,只需在对应的mutation函数里改变state值即可
    - 由于Vue自动重新渲染的特性，无需订阅重新渲染函数，只要生成新的State即可
  - Vuex数据流的顺序是:
    - View调用store.commit提交对应的请求到Store中对应的mutation函数->store改变(vue检测到数据变化自动渲染)
