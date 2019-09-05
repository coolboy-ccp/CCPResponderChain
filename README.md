# CCPResponderChain
iOS事件传递

# 事件类型及其第一响应者

Event Type | First Responder
:-:|:-:
Touch | The view in which the touch occurred
Press | The object that focus
Shake-motion | The object that you (or UIKit) designate
Remote-control | The object that you (or UIKit) designate
Editing menu messages | The object that you (or UIKit) designate

## 解释
* Shake-motion 

Motion events related to the accelerometers, gyroscopes, and magnetometer do not follow the responder chain. Instead, Core Motion delivers those events directly to the designated object.

运动事件和加速器、陀螺仪、地磁仪相关，不遵循响应者链流程。Core motion 直接向指定的对象发送事件.
