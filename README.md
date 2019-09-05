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

## 特别说明
* Shake-motion 

   <br/>Motion events related to the accelerometers, gyroscopes, and magnetometer do not follow the responder chain. Instead, Core     Motion delivers those events directly to the designated object.

   运动事件和加速器、陀螺仪、地磁仪相关，不遵循响应者链流程。Core motion 直接向指定的对象发送事件.
   
* Remote-control

   从外设传递过来的事件，see [Handling External Player Events Notifications](https://developer.apple.com/documentation/mediaplayer/handling_external_player_events_notifications)
   
* Editing menu messages

   Are not events, but they may still take advantage of responder chain.When the target object of a control is nil, UIKit starts from the target object and traverses the responder chain until it finds an object that implements the appropriate action method.
   
   
   编辑菜单消息(长按选择某段文字弹出的菜单栏).当指定的target为空的时候，UIKit会顺着响应链寻找合适的target去处理action。这里合适的target是指响应者链上实现了cut(_:), copy(_:), or paste(_:)的responder。
   
* Touch & Press(3D Touch, iOS9.0+)
   * controls
      Controls communicate directly with their associated target object using action messages. When the user interacts with a control, the control sends an action message to its target object. Action messages are not events, but they may still take advantage of the responder chain. When the target object of a control is nil, UIKit starts from the target object and traverses the responder chain until it finds an object that implements the appropriate action method.
      
      控件使用action messages直接与关联的target联系。当用户与控件交互时，控件发送action messages到target。action messages不是事件，但它们可能会利用响应者链。当target是nil时，UIKit开始从响应者链上寻找合适的响应者。
   * Gesture
      Gesture recognizers receive touch and press events before their view does. If a view's gesture recognizers fail to recognize a sequence of touches, UIKit sends the touches to the view. If the view does not handle the touches, UIKit passes them up the responder chain.[More](https://developer.apple.com/documentation/uikit/touches_presses_and_gestures/handling_uikit_gestures)
      
      手势
      Gesture recognizers receive touch and press events before their view does. If a view's gesture recognizers fail to recognize a sequence of touches, UIKit sends the touches to the view. If the view does not handle the touches, UIKit passes them up the responder chain.[More](https://developer.apple.com/documentation/uikit/touches_presses_and_gestures/handling_uikit_gestures)hu
      Gesture recognizers receive touch and press events before their view does. If a view's gesture recognizers fail to recognize a sequence of touches, UIKit sends the touches to the view. If the view does not handle the touches, UIKit passes them up the responder chain.[More](https://developer.apple.com/documentation/uikit/touches_presses_and_gestures/handling_uikit_gestures)
