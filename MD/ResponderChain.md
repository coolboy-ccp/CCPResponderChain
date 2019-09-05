#  响应者链
## 流程
![Responder Chain](https://github.com/coolboy-ccp/CCPResponderChain/blob/master/PIC/响应者链.png)

## 响应者 
Responder | Next Responder
:-:|:-:
UIView | view controller or superview
UIViewController | window or view controller
UIWindow | UIApplication
UIApplication | AppDelegate
Appdelegate | nil
