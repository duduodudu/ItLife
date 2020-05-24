# swift 杂记

## Selector 
- @selector 可以将一个方法转换并赋值给SEL。
- swift2.2 之后使用 #selector 
- swift4之后需要添加@objc
- 方便使用 可以使用extension。添加
``` swift 
fileprivate extension Selector {
    static let name = #selector(MyClass.method)
    static let updateMainTimer = #selector(ViewController.updateMainTimer)
}
```
## 单例
- OC使用`dispatch_once_t`可以保证里面的代码只被调用一次，以此保证单例在线程上的安全。
``` objc
@implementation MyManager 
+ (instancetype)shared{
    statistatic MyManager * _staticInstance = nil;
    static dispatch_once_t onceToken;

    dispatch_once(&onceToken, ^{
        _staticInstance = [[self alloc] init];
    });
    return _staticInstance;
}
@end 
```
- swift 更简单（移除dispacth_once）
``` swift 
class MyManager {
    static let shared = MyManager()
    private init(){}
}
```
# 条件编译 
- 没有`#ifdef`
- `#if` 用法有限
    `os()`:macOS,iOS,tvOS,watchOS,Linux
    `arch()` x86_64,arm,arm64,i386
    `swift()` >= 某个版本
- 添加自定义编译
`Build Settings` -> `Custom Flags`

## @UIApplicationMain
- 主入口 

## protocol 协议 
没有可选。实现可选方法：
    可以继承`NSObjectProtocol`
    @objc optional
    protocal extension 

## weak & unowned 
swift ARC:
强引用:默认。
弱引用:weak:必须为可选类型的var,会自动将引用设置为nil
无主引用:unowned:不会产生强引用，实例销毁之后任然存储着实例的内存地址。可能会产生野指针。
- weak unowned 都能解决循环引用问题，unownwd消耗小

## 值类型与引用类型 
- swift中值类型，栈区。引用类型，堆区。
- struct enum tuple 都是值类型。
- 值类型为深拷贝 Deep Copy。