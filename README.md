# CCPResponderChain
## 事件处理
### 处理过程
用户与硬件发生交互，操作系统接收到硬件通知，创建对应的事件并将事件传递到当前正在运行的App的事件队列(Runloop)。经过[事件分发](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/MD/EventDeliver.md)找到最佳视图，通过[响应者链](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/MD/ResponderChain.md)找到事件处理者处理事件。
### 处理流程图
![Event Flow](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/PIC/事件流程.png)
---
## 事件类型
### Type & First Responder Table
Event Type | First Responder
:-:|:-:
Touch | The view in which the touch occurred
Press | The object that focus
Shake-motion | The object that you (or UIKit) designate
Remote-control | The object that you (or UIKit) designate
Editing menu messages | The object that you (or UIKit) designate.Not an event.
### Type 
![iOS Event Type](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/PIC/iOS事件类型.png)


