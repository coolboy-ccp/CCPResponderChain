# CCPResponderChain
## 事件产生
用户与硬件发生交互，操作系统接收到硬件通知，创建对应的事件并将事件传递到当前正在运行的App的事件队列(Runloop)。经过[事件分发](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/MD/EventDeliver.md)找到最佳视图，通过[响应者链](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/MD/ResponderChain.md)找到事件处理者。
## 事件类型
<br/>[Event Type](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/MD/EventType.md)
## 事件流程
![Event Flow](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/PIC/事件流程.png)
