---
layout: mypost
title: UIViewController的生命周期
date:   2020-11-03 18:28:00
categories: [iOS]
---

### Xcode11

Xcode11新建项目会多出SceneDelegate这个类，然后在低于iOS13的真机下运行会黑屏，是因为iOS13以下没有UIScene这一层，需要在AppDelegate中添加一行代码：

```objc
@interface AppDelegate ()<UNUserNotificationCenterDelegate>

@end

@implementation AppDelegate

@synthesize window = _window; // 这一行

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {}
...
```

参考资料：

[iOS13 ，xcode11新建项目真机运行出现黑屏及新出现的SceneDelegate的作用](https://www.jianshu.com/p/95533368e4f9)

### UIScene的执行顺序

现在的逻辑是AppDelegate管理单个或多个UIScene，UIScene管理单个或多个UIWindow：

```objc
- (void)scene:(UIScene *)scene willConnectToSession:(UISceneSession *)session options:(UISceneConnectionOptions *)connectionOptions  API_AVAILABLE(ios(13.0)){
    NSLog(@"连接UIScene场景，也可能是断开后的重新连接");
}
- (void)sceneDidDisconnect:(UIScene *)scene  API_AVAILABLE(ios(13.0)){
    NSLog(@"与场景断开");
}
- (void)sceneDidBecomeActive:(UIScene *)scene  API_AVAILABLE(ios(13.0)){
    NSLog(@"app进入活动状态，在这里继续未开始的或被暂停的任务");
}
- (void)sceneWillResignActive:(UIScene *)scene  API_AVAILABLE(ios(13.0)){
    NSLog(@"app从活动切换到非活动状态，可能是由于临时中断如来电造成");
}
- (void)sceneWillEnterForeground:(UIScene *)scene  API_AVAILABLE(ios(13.0)){
    NSLog(@"app即将进入前台");
}
- (void)sceneDidEnterBackground:(UIScene *)scene  API_AVAILABLE(ios(13.0)){
    NSLog(@"app进入后台");
}
```

[iOS应用程序生命周期(前后台切换,应用的各种状态)详解](https://blog.csdn.net/totogo2010/article/details/8048652)

#### UIViewController的声明周期

```objc
- (void)viewDidLoad {
    [super viewDidLoad];
    NSLog(@"初始化，仅执行一次");
}
- (void)viewWillAppear:(BOOL)animated {
    [super viewWillAppear:animated];
    NSLog(@"视图即将出现，可能执行多次");
}
- (void)viewDidAppear:(BOOL)animated {
    [super viewDidAppear:animated];
    NSLog(@"视图完全过渡到界面上，可能执行多次");
}
- (void)viewWillDisappear:(BOOL)animated {
    [super viewWillDisappear:animated];
    NSLog(@"视图即将消失，可能执行多次");
}
- (void)viewDidDisappear:(BOOL)animated {
    [super viewDidDisappear:animated];
    NSLog(@"视图完全消失，可能执行多次");
}
- (void)dealloc {
    NSLog(@"被释放");
}
```
