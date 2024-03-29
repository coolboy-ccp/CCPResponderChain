#  Event Deliver
## 事件分发
### 不能处理事件的视图
* super view 不能处理事件
* userInteractionEnabled == false
* isHidden == true
* alpha <= 0.01
* frame超出父视图bounds，且父视图的clipToBounds == false
### Hit-Test
1. UIApplication从事件队列中取出头部事件分发到keyWindow
2. UIWindow会调用hitTest:withEvent:方法在视图层次结构中找到一个最合适的UIView来处理这个事件；分发的顺序和响应链基本相反：UIApplication -> UIWindow -> Root View -> ··· -> subview：
3. 调用当前视图的hitTest:withEvent:，出现***不能处理事件的视图***，return nil
4. 调用当前视图的pointInside:withEvent:,return NO， hitTest:withEvent: return nil
5. 倒序遍历子视图，重复3，4，直到有子视图的hitTest:withEvent:方法返回非空对象或者全部子视图遍历完毕
6. 若所有子视图的hitTest:withEvent:方法都返回nil（触摸点不在子视图上），则当前视图的hitTest:withEvent:方法返回当前视图；
7. 若有子视图的hitTest:withEvent:方法返回非空对象（第一响应对象为子视图），则当前视图的hitTest:withEvent:方法就返回此对象，处理结束。
---
## 特殊事件
* [Motion](https://developer.apple.com/documentation/coremotion)
<br/>Motion events related to the accelerometers, gyroscopes, and magnetometer do not follow the responder chain. Instead, Core     Motion delivers those events directly to the designated object.See [Core Motion Framework](https://developer.apple.com/documentation/#//apple_ref/doc/uid/TP40007898-CH10-SW27)
<br/>运动事件和加速器、陀螺仪、地磁仪相关，不遵循响应者链流程。Core motion 直接向指定的对象发送事件.
* Remote-control
<br/>从外设传递过来的事件，see [Handling External Player Events Notifications](https://developer.apple.com/documentation/mediaplayer/handling_external_player_events_notifications)
* Editing menu messages
<br/>Are not events, but they may still take advantage of responder chain.When the target object of a control is nil, UIKit starts from the target object and traverses the responder chain until it finds an object that implements the appropriate action method.   
<br/>编辑菜单消息(长按选择某段文字弹出的菜单栏).当指定的target为空的时候，UIKit会顺着响应链寻找合适的target去处理action。这里合适的target是指响应者链上实现了[cut(_:)](https://developer.apple.com/documentation/uikit/uiresponderstandardeditactions/2354193-cut), [copy(_:)](https://developer.apple.com/documentation/uikit/uiresponderstandardeditactions/2354191-copy), [paste(_:)](https://developer.apple.com/documentation/uikit/uiresponderstandardeditactions/2354189-paste)等的responder。
* Touch & Press(3D Touch, iOS9.0+)
   * [Control](https://developer.apple.com/documentation/uikit/uicontrol)
   <br/>Controls communicate directly with their associated target object using action messages. When the user interacts with a control, the control sends an action message to its target object. Action messages are not events, but they may still take advantage of the responder chain. When the target object of a control is nil, UIKit starts from the target object and traverses the responder chain until it finds an object that implements the appropriate action method.
<br/> 控件使用action messages直接与关联的target联系。当用户与控件交互时，控件发送action messages到target。action messages不是事件，但它们可能会利用响应者链。当target是nil时，UIKit开始从响应者链上寻找合适的响应者。
   * [Gesture](https://developer.apple.com/documentation/uikit/uigesturerecognizer)
   <br/>Gesture recognizers receive touch and press events before their view does. If a view's gesture recognizers fail to recognize a sequence of touches, UIKit sends the touches to the view. If the view does not handle the touches, UIKit passes them up the responder chain.[More](https://developer.apple.com/documentation/uikit/touches_presses_and_gestures/handling_uikit_gestures)
<br/>手势识别在view之前接收到touch和press。如果一个view的手势无法识别一系列的touches，UIKit将touches发送给view。如果view没有处理touches，UIKit通过响应者链传递。

