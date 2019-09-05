#  响应者链
## 链图
![Responder Chain](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/PIC/响应者链.png)

## 响应者 
Responder | Next Responder
:-:|:-:
UIView | view controller or superview
UIViewController | window or view controller
UIWindow | UIApplication
UIApplication | AppDelegate
AppDelegate | nil
### 说明
* UIView 
   * The root view of a view controller, the next responder is the view controller
   * The next responder is view's superview
* UIViewController 
   * It's view is the root view of a window, the next responder is the window object
   * The presenting view
* UIApplication
   * The next responder is the app delegate, but only if the app delegate is an instance of UIResponder and is not a view, view controller, or the app object itself.
---
## 事件处理
1. 如果当前responder不能处理事件，传递给下一个responder
2. 循环1，直到找到可以处理事件的responder
3. 到UIApplication还不能处理事件时，丢弃该事件

