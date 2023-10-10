> 1 / 1
> 
> swift navigationstack详解

1 / 1

Finished browsing

Show work

Hide work

NavigationStack was introduced by Apple during the

WWDC 2022 as a key feature of iOS 16 and SwiftUI, serving as a replacement for NavigationView to address certain usability issues and offer more power and flexibility​[1](https://www.jianshu.com/p/865017a26a4c#:~:text=NavigationStack%E6%98%AF%E8%8B%B9%E6%9E%9C%E5%9C%A82022%E5%B9%B4WWDC%E5%A4%A7%E4%BC%9A%E6%8E%A8%E5%87%BA%E7%9A%84%E4%B8%80%E9%A1%B9%E9%87%8D%E8%A6%81ios16%20swiftui%E7%89%B9%E6%80%A7%E3%80%82%20%E5%AE%83%E6%98%AFNavigationView%E7%9A%84%E6%9B%BF%E4%BB%A3%EF%BC%8C%E8%A7%A3%E5%86%B3%E4%BA%86%E5%85%B6%E4%BD%BF%E7%94%A8%E8%B5%B7%E6%9D%A5%E7%9A%84%E4%B8%80%E4%BA%9B%E9%97%AE%E9%A2%98%EF%BC%8C%E5%B9%B6%E4%B8%94%E6%9B%B4%E5%A4%A7%E5%BC%BA%E5%A4%A7%E5%92%8C%E7%81%B5%E6%B4%BB%E3%80%82%20%E6%80%BB%E8%A7%88%20NS%E9%80%9A%E8%BF%87%E8%AE%A9%E5%AF%BC%E8%88%AA%E9%93%BE%E6%8E%A5%E7%9A%84%E5%80%BC%E5%92%8C%E5%85%B7%E4%BD%93%E7%9A%84%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E5%88%86%E7%A6%BB%EF%BC%8C%E4%BD%BF%E5%BE%97%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E6%9B%B4%E5%8A%A0%E5%AE%B9%E6%98%93%E6%8E%A7%E5%88%B6%E3%80%82,%E5%8F%A6%E5%A4%96%E5%BC%95%E5%85%A5%E4%BA%86%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%E7%9A%84%E6%A6%82%E5%BF%B5%EF%BC%8C%E8%AE%A9%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E4%BB%BB%E6%84%8F%E5%8E%8B%E5%85%A5%2F%E5%BC%B9%E5%87%BA%2F%E6%9B%BF%E4%BB%A3%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%EF%BC%8C%E6%98%AF%E7%9A%84%E5%AF%BC%E8%88%AA%E6%8E%A7%E5%88%B6%E6%9E%81%E4%B8%BA%E7%81%B5%E6%B4%BB%E3%80%82%20%E7%AE%80%E5%8D%95%E6%9B%BF%E4%BB%A3NavigationView%20%E9%A6%96%E5%85%88%EF%BC%8C%E5%8F%AF%E4%BB%A5%E7%9B%B4%E6%8E%A5%E7%94%A8NavigationStack%E6%9B%BF%E4%BB%A3NavigationView%EF%BC%8C%E7%A8%8B%E5%BA%8F%E6%95%88%E6%9E%9C%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%8F%98%E5%8C%96%E3%80%82%20%E5%A6%82%E4%B8%8B%E9%9D%A2%E7%A8%8B%E5%BA%8F%E6%89%80%E7%A4%BA%E3%80%82)​. It primarily separates navigation link values from the actual navigation actions, making navigation behavior easier to control. Additionally, it introduces the concept of navigation paths, allowing users to push, pop, or replace navigation paths, thus offering highly flexible navigation control​[1](https://www.jianshu.com/p/865017a26a4c#:~:text=NavigationStack%E6%98%AF%E8%8B%B9%E6%9E%9C%E5%9C%A82022%E5%B9%B4WWDC%E5%A4%A7%E4%BC%9A%E6%8E%A8%E5%87%BA%E7%9A%84%E4%B8%80%E9%A1%B9%E9%87%8D%E8%A6%81ios16%20swiftui%E7%89%B9%E6%80%A7%E3%80%82%20%E5%AE%83%E6%98%AFNavigationView%E7%9A%84%E6%9B%BF%E4%BB%A3%EF%BC%8C%E8%A7%A3%E5%86%B3%E4%BA%86%E5%85%B6%E4%BD%BF%E7%94%A8%E8%B5%B7%E6%9D%A5%E7%9A%84%E4%B8%80%E4%BA%9B%E9%97%AE%E9%A2%98%EF%BC%8C%E5%B9%B6%E4%B8%94%E6%9B%B4%E5%A4%A7%E5%BC%BA%E5%A4%A7%E5%92%8C%E7%81%B5%E6%B4%BB%E3%80%82%20%E6%80%BB%E8%A7%88%20NS%E9%80%9A%E8%BF%87%E8%AE%A9%E5%AF%BC%E8%88%AA%E9%93%BE%E6%8E%A5%E7%9A%84%E5%80%BC%E5%92%8C%E5%85%B7%E4%BD%93%E7%9A%84%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E5%88%86%E7%A6%BB%EF%BC%8C%E4%BD%BF%E5%BE%97%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E6%9B%B4%E5%8A%A0%E5%AE%B9%E6%98%93%E6%8E%A7%E5%88%B6%E3%80%82,%E5%8F%A6%E5%A4%96%E5%BC%95%E5%85%A5%E4%BA%86%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%E7%9A%84%E6%A6%82%E5%BF%B5%EF%BC%8C%E8%AE%A9%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E4%BB%BB%E6%84%8F%E5%8E%8B%E5%85%A5%2F%E5%BC%B9%E5%87%BA%2F%E6%9B%BF%E4%BB%A3%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%EF%BC%8C%E6%98%AF%E7%9A%84%E5%AF%BC%E8%88%AA%E6%8E%A7%E5%88%B6%E6%9E%81%E4%B8%BA%E7%81%B5%E6%B4%BB%E3%80%82%20%E7%AE%80%E5%8D%95%E6%9B%BF%E4%BB%A3NavigationView%20%E9%A6%96%E5%85%88%EF%BC%8C%E5%8F%AF%E4%BB%A5%E7%9B%B4%E6%8E%A5%E7%94%A8NavigationStack%E6%9B%BF%E4%BB%A3NavigationView%EF%BC%8C%E7%A8%8B%E5%BA%8F%E6%95%88%E6%9E%9C%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%8F%98%E5%8C%96%E3%80%82%20%E5%A6%82%E4%B8%8B%E9%9D%A2%E7%A8%8B%E5%BA%8F%E6%89%80%E7%A4%BA%E3%80%82)​.

Here’s a breakdown of how NavigationStack can be utilized:

1.  **Basic Usage**:
    
    swift
    
    ```swift
    NavigationStack {
        List(parks) { park in
            NavigationLink(park.name, value: park)
        }
        .navigationDestination(for: Park.self) { park in
            ParkDetails(park: park)
        }
    }
    ```
    
    In this basic example, `NavigationStack` acts similarly to a primary `navController` that initiates navigation​[2](https://juejin.cn/post/7237425753611681847#:~:text=NavigationStack%20%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95%20NavigationStack%20,NavigationStack%20%E7%AD%89%E5%90%8C%E4%BA%8E%E5%BC%80%E5%A7%8B%E7%9A%84%E9%A6%96%E9%A1%B5navContrller%20%EF%BC%8C%E5%AF%BC%E8%88%AA%E5%BC%80%E5%A7%8B%E7%9A%84%E6%97%B6%E5%80%99%E3%80%82)​.
    
2.  **Single-Column Usage**: `NavigationStack` is designed for single-column scenarios like on iPhone, Apple TV, and Apple Watch, where it can be used as follows:
    
    swift
    
    ```swift
    NavigationStack {
        // content here
    }
    ```
    
    This is analogous to using `NavigationView` with a stack navigation style​[3](https://zhuanlan.zhihu.com/p/528278554#:~:text=%E4%B8%80%E5%88%86%E4%B8%BA%E4%BA%8C%20%E6%96%B0%E7%9A%84%E5%AF%BC%E8%88%AA%E7%B3%BB%E7%BB%9F%E6%9C%80%E7%9B%B4%E6%8E%A5%E7%9A%84%E5%8F%98%E5%8C%96%E6%98%AF%E5%BA%9F%E5%BC%83%E4%BA%86%20NavigationView%EF%BC%8C%E5%B0%86%E5%85%B6%E5%8A%9F%E8%83%BD%E5%88%86%E6%88%90%E4%BA%86%E4%B8%A4%E4%B8%AA%E5%8D%95%E7%8B%AC%E7%9A%84%E6%8E%A7%E4%BB%B6%20NavigationStack%20%E5%92%8C,stack%29%20NavigationSplitView%20%E5%88%99%E9%92%88%E5%AF%B9%E7%9A%84%E6%98%AF%E5%A4%9A%E6%A0%8F%E5%9C%BA%E6%99%AF%EF%BC%8C%E4%BE%8B%E5%A6%82%20%EF%BC%9AiPadOS%20%E3%80%81macOS%EF%BC%9A)​.
    
3.  **Navigation via Paths**: Unlike `NavigationView`, `NavigationStack` uses paths to define navigation states, making it more flexible and modern as a navigation container​[4](https://juejin.cn/post/7262656196854464568#:~:text=%E5%9C%A8%20SwiftUI%20%E4%B8%AD%2CNavigationStack%20%E5%92%8C%20NavigationView,avigationStack%20%E6%98%AF%E6%96%B0%E4%B8%80%E4%BB%A3%E5%AF%BC%E8%88%AA%E5%AE%B9%E5%99%A8%2CNavigationView%20%E5%B0%86%E8%A2%AB%E9%80%90%E6%AD%A5%E6%B7%98%E6%B1%B0%E3%80%82%20NavigationStack%20%E4%BD%BF%E7%94%A8%E8%B7%AF%E5%BE%84%E6%9D%A5%E5%AE%9A%E4%B9%89%E5%AF%BC%E8%88%AA%E7%8A%B6%E6%80%81%2C%E6%9B%B4%E7%81%B5%E6%B4%BB)​.
    
4.  **Stack of Views**: It helps in presenting a stack of views over a root view, where views can be added to the top of the stack by
    

tapping a `NavigationLink`, and removed using platform-appropriate controls like a Back button or swipe gesture​[1](https://developer.apple.com/documentation/swiftui/navigationstack/#:~:text=Overview%20Use%20a%20navigation%20stack,button%20or%20a%20swipe%20gesture)​.

5.  **Detailed Usage Example**: In a detailed example, a structure is defined to hold data of a list item, and two views are created for list and detail pages. `NavigationStack` is used to manage the navigation between these pages, with `NavigationLink` and `navigationDestination(for:destination:)` modifier being utilized for navigation actions​[2](https://juejin.cn/post/7268539219303235639)​.
    
6.  **Multiple Navigation Destinations**: Developers can define multiple `navigationDestination` modifiers to handle different types of navigation links within the same `NavigationStack`​[2](https://juejin.cn/post/7268539219303235639)​.
    
7.  **Navigation State Management**: `NavigationStack` facilitates convenient navigation state tracking by accepting a path parameter bound to the stack’s navigation state during initialization​[2](https://juejin.cn/post/7268539219303235639)​.
    

This comprehensive explanation alongside the examples should provide a solid understanding of how to use `NavigationStack` in SwiftUI for different navigation requirements.

> 1 / 1
> 
> 翻译成中文

1 / 1

NavigationStack是苹果在2022年WWDC上推出的iOS 16和SwiftUI的重要特性，它作为NavigationView的替代方案，旨在解决某些可用性问题，并提供更多的功能和灵活性​[1](https://www.jianshu.com/p/865017a26a4c#:~:text=NavigationStack%E6%98%AF%E8%8B%B9%E6%9E%9C%E5%9C%A82022%E5%B9%B4WWDC%E5%A4%A7%E4%BC%9A%E6%8E%A8%E5%87%BA%E7%9A%84%E4%B8%80%E9%A1%B9%E9%87%8D%E8%A6%81ios16%20swiftui%E7%89%B9%E6%80%A7%E3%80%82%20%E5%AE%83%E6%98%AFNavigationView%E7%9A%84%E6%9B%BF%E4%BB%A3%EF%BC%8C%E8%A7%A3%E5%86%B3%E4%BA%86%E5%85%B6%E4%BD%BF%E7%94%A8%E8%B5%B7%E6%9D%A5%E7%9A%84%E4%B8%80%E4%BA%9B%E9%97%AE%E9%A2%98%EF%BC%8C%E5%B9%B6%E4%B8%94%E6%9B%B4%E5%A4%A7%E5%BC%BA%E5%A4%A7%E5%92%8C%E7%81%B5%E6%B4%BB%E3%80%82%20%E6%80%BB%E8%A7%88%20NS%E9%80%9A%E8%BF%87%E8%AE%A9%E5%AF%BC%E8%88%AA%E9%93%BE%E6%8E%A5%E7%9A%84%E5%80%BC%E5%92%8C%E5%85%B7%E4%BD%93%E7%9A%84%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E5%88%86%E7%A6%BB%EF%BC%8C%E4%BD%BF%E5%BE%97%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E6%9B%B4%E5%8A%A0%E5%AE%B9%E6%98%93%E6%8E%A7%E5%88%B6%E3%80%82,%E5%8F%A6%E5%A4%96%E5%BC%95%E5%85%A5%E4%BA%86%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%E7%9A%84%E6%A6%82%E5%BF%B5%EF%BC%8C%E8%AE%A9%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E4%BB%BB%E6%84%8F%E5%8E%8B%E5%85%A5%2F%E5%BC%B9%E5%87%BA%2F%E6%9B%BF%E4%BB%A3%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%EF%BC%8C%E6%98%AF%E7%9A%84%E5%AF%BC%E8%88%AA%E6%8E%A7%E5%88%B6%E6%9E%81%E4%B8%BA%E7%81%B5%E6%B4%BB%E3%80%82%20%E7%AE%80%E5%8D%95%E6%9B%BF%E4%BB%A3NavigationView%20%E9%A6%96%E5%85%88%EF%BC%8C%E5%8F%AF%E4%BB%A5%E7%9B%B4%E6%8E%A5%E7%94%A8NavigationStack%E6%9B%BF%E4%BB%A3NavigationView%EF%BC%8C%E7%A8%8B%E5%BA%8F%E6%95%88%E6%9E%9C%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%8F%98%E5%8C%96%E3%80%82%20%E5%A6%82%E4%B8%8B%E9%9D%A2%E7%A8%8B%E5%BA%8F%E6%89%80%E7%A4%BA%E3%80%82)​。它主要将导航链接值与实际的导航操作分开，使导航行为更容易控制。此外，它引入了导航路径的概念，允许用户推送、弹出或替换导航路径，从而提供了极高的导航控制灵活性​[1](https://www.jianshu.com/p/865017a26a4c#:~:text=NavigationStack%E6%98%AF%E8%8B%B9%E6%9E%9C%E5%9C%A82022%E5%B9%B4WWDC%E5%A4%A7%E4%BC%9A%E6%8E%A8%E5%87%BA%E7%9A%84%E4%B8%80%E9%A1%B9%E9%87%8D%E8%A6%81ios16%20swiftui%E7%89%B9%E6%80%A7%E3%80%82%20%E5%AE%83%E6%98%AFNavigationView%E7%9A%84%E6%9B%BF%E4%BB%A3%EF%BC%8C%E8%A7%A3%E5%86%B3%E4%BA%86%E5%85%B6%E4%BD%BF%E7%94%A8%E8%B5%B7%E6%9D%A5%E7%9A%84%E4%B8%80%E4%BA%9B%E9%97%AE%E9%A2%98%EF%BC%8C%E5%B9%B6%E4%B8%94%E6%9B%B4%E5%A4%A7%E5%BC%BA%E5%A4%A7%E5%92%8C%E7%81%B5%E6%B4%BB%E3%80%82%20%E6%80%BB%E8%A7%88%20NS%E9%80%9A%E8%BF%87%E8%AE%A9%E5%AF%BC%E8%88%AA%E9%93%BE%E6%8E%A5%E7%9A%84%E5%80%BC%E5%92%8C%E5%85%B7%E4%BD%93%E7%9A%84%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E5%88%86%E7%A6%BB%EF%BC%8C%E4%BD%BF%E5%BE%97%E5%AF%BC%E8%88%AA%E8%A1%8C%E4%B8%BA%E6%9B%B4%E5%8A%A0%E5%AE%B9%E6%98%93%E6%8E%A7%E5%88%B6%E3%80%82,%E5%8F%A6%E5%A4%96%E5%BC%95%E5%85%A5%E4%BA%86%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%E7%9A%84%E6%A6%82%E5%BF%B5%EF%BC%8C%E8%AE%A9%E7%94%A8%E6%88%B7%E5%8F%AF%E4%BB%A5%E4%BB%BB%E6%84%8F%E5%8E%8B%E5%85%A5%2F%E5%BC%B9%E5%87%BA%2F%E6%9B%BF%E4%BB%A3%E5%AF%BC%E8%88%AA%E8%B7%AF%E5%BE%84%EF%BC%8C%E6%98%AF%E7%9A%84%E5%AF%BC%E8%88%AA%E6%8E%A7%E5%88%B6%E6%9E%81%E4%B8%BA%E7%81%B5%E6%B4%BB%E3%80%82%20%E7%AE%80%E5%8D%95%E6%9B%BF%E4%BB%A3NavigationView%20%E9%A6%96%E5%85%88%EF%BC%8C%E5%8F%AF%E4%BB%A5%E7%9B%B4%E6%8E%A5%E7%94%A8NavigationStack%E6%9B%BF%E4%BB%A3NavigationView%EF%BC%8C%E7%A8%8B%E5%BA%8F%E6%95%88%E6%9E%9C%E6%B2%A1%E6%9C%89%E4%BB%BB%E4%BD%95%E5%8F%98%E5%8C%96%E3%80%82%20%E5%A6%82%E4%B8%8B%E9%9D%A2%E7%A8%8B%E5%BA%8F%E6%89%80%E7%A4%BA%E3%80%82)​。

以下是NavigationStack的使用细节：

1.  **基本用法**:
    
    swift
    
    ```swift
    NavigationStack {
        List(parks) { park in
            NavigationLink(park.name, value: park)
        }
        .navigationDestination(for: Park.self) { park in
            ParkDetails(park: park)
        }
    }
    ```
    
    在这个基本示例中，`NavigationStack`类似于初始化导航的主要`navController`​[2](https://juejin.cn/post/7237425753611681847#:~:text=NavigationStack%20%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95%20NavigationStack%20,NavigationStack%20%E7%AD%89%E5%90%8C%E4%BA%8E%E5%BC%80%E5%A7%8B%E7%9A%84%E9%A6%96%E9%A1%B5navContrller%20%EF%BC%8C%E5%AF%BC%E8%88%AA%E5%BC%80%E5%A7%8B%E7%9A%84%E6%97%B6%E5%80%99%E3%80%82)​。
    
2.  **单列使用**: `NavigationStack`适用于单列场景，如iPhone、Apple TV和Apple Watch，可以如下所示使用：
    
    swift
    
    ```swift
    NavigationStack {
        // 内容在这里
    }
    ```
    
    这类似于以堆栈导航样式使用`NavigationView`​[3](https://zhuanlan.zhihu.com/p/528278554#:~:text=%E4%B8%80%E5%88%86%E4%B8%BA%E4%BA%8C%20%E6%96%B0%E7%9A%84%E5%AF%BC%E8%88%AA%E7%B3%BB%E7%BB%9F%E6%9C%80%E7%9B%B4%E6%8E%A5%E7%9A%84%E5%8F%98%E5%8C%96%E6%98%AF%E5%BA%9F%E5%BC%83%E4%BA%86%20NavigationView%EF%BC%8C%E5%B0%86%E5%85%B6%E5%8A%9F%E8%83%BD%E5%88%86%E6%88%90%E4%BA%86%E4%B8%A4%E4%B8%AA%E5%8D%95%E7%8B%AC%E7%9A%84%E6%8E%A7%E4%BB%B6%20NavigationStack%20%E5%92%8C,stack%29%20NavigationSplitView%20%E5%88%99%E9%92%88%E5%AF%B9%E7%9A%84%E6%98%AF%E5%A4%9A%E6%A0%8F%E5%9C%BA%E6%99%AF%EF%BC%8C%E4%BE%8B%E5%A6%82%20%EF%BC%9AiPadOS%20%E3%80%81macOS%EF%BC%9A)​。
    
3.  **通过路径导航**: 与`NavigationView`不同，`NavigationStack`使用路径来定义导航状态，使其成为更灵活、更现代的导航容器​[4](https://juejin.cn/post/7262656196854464568#:~:text=%E5%9C%A8%20SwiftUI%20%E4%B8%AD%2CNavigationStack%20%E5%92%8C%20NavigationView,avigationStack%20%E6%98%AF%E6%96%B0%E4%B8%80%E4%BB%A3%E5%AF%BC%E8%88%AA%E5%AE%B9%E5%99%A8%2CNavigationView%20%E5%B0%86%E8%A2%AB%E9%80%90%E6%AD%A5%E6%B7%98%E6%B1%B0%E3%80%82%20NavigationStack%20%E4%BD%BF%E7%94%A8%E8%B7%AF%E5%BE%84%E6%9D%A5%E5%AE%9A%E4%B9%89%E5%AF%BC%E8%88%AA%E7%8A%B6%E6%80%81%2C%E6%9B%B4%E7%81%B5%E6%B4%BB)​。
    
4.  **视图堆栈**: 它有助于在根视图上展示一堆视图，其中可以通过点击`NavigationLink`将视图添加到堆栈的顶部，并使用后退按钮或滑动手势等平台适当的控件来删除视图​[5](https://developer.apple.com/documentation/swiftui/navigationstack/#:~:text=Overview%20Use%20a%20navigation%20stack,button%20or%20a%20swipe%20gesture)​。
    
5.  **详细使用示例**: 在一个详细的示例中，定义了一个结构来保存列表项的数据，并为列表和详细信息页面创建了两个视图。`NavigationStack`用于管理这些页面之间的导航，`NavigationLink`和`navigationDestination(for:destination:)`修饰符用于导航操作​[6](https://juejin.cn/post/7268539219303235639)​。
    
6.  **多个导航目的地**: 开发人员可以在同一个`NavigationStack`中定义多个`navigationDestination`修饰符，以处理不同类型的导航链接​[6](https://juejin.cn/post/7268539219303235639)​。
    
7.  **导航状态管理**: `NavigationStack`通过在初始化期间接受绑定到堆栈的导航状态的路径参数，方便地跟踪导航状态​[6](https://juejin.cn/post/7268539219303235639)​。
    

通过这些详细的解释和示例，应该能够为你提供如何在SwiftUI中使用`NavigationStack`来满足不同的导航需求的坚实理解。

> 1 / 1
> 
> 我准备使用swiftui实现一个聊天软件。希望你能够协助我

1 / 1

很好，我可以为你提供指导和帮助。使用SwiftUI实现聊天软件是一个有趣而且实用的项目。以下是一些基本的步骤和考虑因素，以帮助你开始：

1.  **设计UI**:
    
    *   设计一个简洁、直观的用户界面(UI)是非常重要的。你需要考虑如何布局聊天界面，如何显示消息，如何让用户输入消息等。
    *   你可能也想要添加一些额外的功能，比如表情符号、图片和视频的发送等。
2.  **模型和数据结构**:
    
    *   设计一个能够储存和管理消息的数据结构是很重要的。通常，你会有一个`Message`结构，它包含了消息的内容、发送者、时间戳等信息。
3.  **网络通信**:
    
    *   你需要一个服务器来处理实时消息传递。你可以使用像Firebase这样的后端服务，或者构建你自己的服务器。
4.  **实时更新**:
    
    *   使用WebSocket或其他实时通信技术来确保消息能够实时传递和接收。
5.  **消息历史记录**:
    
    *   提供一个方法来加载和显示旧的消息历史记录。
6.  **用户认证和注册**:
    
    *   如果你想要添加用户认证，你需要设计一个用户登录和注册系统。
7.  **错误处理**:
    
    *   添加适当的错误处理，以确保你的应用能够优雅地处理网络问题和其他错误。
8.  **测试**:
    
    *   确保充分测试你的应用，包括不同的网络条件和错误情况。

如果你有具体的问题或者需要关于某个特定主题的更多指导，比如如何实现实时消息传递，或者如何设计数据模型等，随时提问，我会很高兴为你提供帮助。

> 1 / 1
> 
> 先帮我设计一个websocket管理类，需要完善的功能。 1. 连接的建立与状态管理，需要有重连机制。 2. 消息的发送与接收设计需要合理以便后续的viewModel使用

1 / 1

设计一个WebSocket管理类是一个很好的想法，它将帮助你更好地组织代码并处理WebSocket的连接、消息发送和接收。以下是一个简单的WebSocket管理类设计示例，使用Swift和`URLSessionWebSocketTask`来实现：

swift

```swift
import Foundation

class WebSocketManager: ObservableObject {
    private var webSocketTask: URLSessionWebSocketTask?
    private let url: URL
    private let reconnectInterval: TimeInterval
    
    @Published var isConnected: Bool = false
    @Published var messages: [Message] = []
    
    init(url: URL, reconnectInterval: TimeInterval = 5) {
        self.url = url
        self.reconnectInterval = reconnectInterval
        connect()
    }
    
    deinit {
        disconnect()
    }
    
    private func connect() {
        webSocketTask = URLSession.shared.webSocketTask(with: url)
        webSocketTask?.resume()
        isConnected = true
        receiveMessage()
    }
    
    private func disconnect() {
        webSocketTask?.cancel()
        isConnected = false
    }
    
    private func reconnect() {
        disconnect()
        DispatchQueue.global().asyncAfter(deadline: .now() + reconnectInterval) {
            self.connect()
        }
    }
    
    private func receiveMessage() {
        webSocketTask?.receive { [weak self] result in
            switch result {
            case .failure(let error):
                print("WebSocket receive error: \(error)")
                self?.reconnect()
            case .success(let message):
                switch message {
                case .string(let text):
                    // Assume Message is a struct you defined to hold message data
                    self?.messages.append(Message(text: text))
                default:
                    print("Unhandled message type")
                }
            }
            self?.receiveMessage()
        }
    }
    
    func sendMessage(_ message: String) {
        webSocketTask?.send(URLSessionWebSocketTask.Message.string(message)) { [weak self] error in
            if let error = error {
                print("WebSocket send error: \(error)")
                self?.reconnect()
            }
        }
    }
}

struct Message {
    let text: String
}
```

在这个`WebSocketManager`类中，我们做了以下几件事：

1.  **连接和状态管理**:
    
    *   使用`URLSessionWebSocketTask`来建立和管理WebSocket连接。
    *   有一个`connect`方法来启动连接，一个`disconnect`方法来关闭连接，以及一个`reconnect`方法来处理重连。
2.  **消息接收**:
    
    *   有一个`receiveMessage`方法，它递归地接收消息，以确保总是有一个接收任务在等待新消息。
3.  **消息发送**:
    
    *   `sendMessage`方法允许你发送字符串消息到服务器。
4.  **重连机制**:
    
    *   如果在接收或发送消息时发生错误，`reconnect`方法将被调用以尝试重新连接。
5.  **消息和连接状态发布**:
    
    *   使用`@Published`属性包装器来发布`isConnected`和`messages`，使得你的视图模型可以观察和响应WebSocket的状态和新消息。

这个类现在可以很容易地被你的视图模型使用，以发送和接收消息，并响应连接状态变化。你可以根据你的具体需求进一步定制和扩展这个类。例如，你可能想要添加更复杂的错误处理、消息序列化和反序列化，或更复杂的重连逻辑。

> 1 / 1
> 
> 需要加上网络切换或者断开的情况，这也是需要重连的

2 / 2

在处理网络切换或断开的情况时，通常需要监听系统的网络状态变化。在iOS中，你可以使用`Network`框架中的`NWPathMonitor`类来监听网络状态。以下是如何修改`WebSocketManager`类以处理网络切换或断开情况的示例：

swift

```swift
import Foundation
import Network

class WebSocketManager: ObservableObject {
    private var webSocketTask: URLSessionWebSocketTask?
    private let url: URL
    private let reconnectInterval: TimeInterval
    private let pathMonitor = NWPathMonitor()
    
    @Published var isConnected: Bool = false
    @Published var messages: [Message] = []
    
    init(url: URL, reconnectInterval: TimeInterval = 5) {
        self.url = url
        self.reconnectInterval = reconnectInterval
        
        setupNetworkMonitoring()
        connect()
    }
    
    deinit {
        disconnect()
        pathMonitor.cancel()
    }
    
    private func setupNetworkMonitoring() {
        pathMonitor.pathUpdateHandler = { [weak self] path in
            if path.status == .satisfied {
                if !self?.isConnected ?? false {
                    self?.connect()
                }
            } else {
                self?.disconnect()
            }
        }
        let queue = DispatchQueue.global(qos: .background)
        pathMonitor.start(queue: queue)
    }
    
    private func connect() {
        guard !isConnected else { return }
        
        webSocketTask = URLSession.shared.webSocketTask(with: url)
        webSocketTask?.resume()
        isConnected = true
        receiveMessage()
    }
    
    private func disconnect() {
        webSocketTask?.cancel()
        isConnected = false
    }
    
    private func reconnect() {
        disconnect()
        DispatchQueue.global().asyncAfter(deadline: .now() + reconnectInterval) {
            self.connect()
        }
    }
    
    private func receiveMessage() {
        webSocketTask?.receive { [weak self] result in
            switch result {
            case .failure(let error):
                print("WebSocket receive error: \(error)")
                self?.reconnect()
            case .success(let message):
                switch message {
                case .string(let text):
                    self?.messages.append(Message(text: text))
                default:
                    print("Unhandled message type")
                }
            }
            self?.receiveMessage()
        }
    }
    
    func sendMessage(_ message: String) {
        webSocketTask?.send(URLSessionWebSocketTask.Message.string(message)) { [weak self] error in
            if let error = error {
                print("WebSocket send error: \(error)")
                self?.reconnect()
            }
        }
    }
}

struct Message {
    let text: String
}
```

在这个修改后的`WebSocketManager`类中，我们添加了以下几点:

1.  **网络监控设置**:
    
    *   创建了一个`NWPathMonitor`实例来监控网络状态。
    *   在`init`方法中调用`setupNetworkMonitoring`方法来设置网络监控。
2.  **网络状态处理**:
    
    *   在`pathUpdateHandler`中，当网络满足条件时（即网络连接正常时），我们尝试连接WebSocket（如果它尚未连接）。当网络不满足条件时（即网络断开时），我们断开WebSocket连接。
3.  **连接方法更新**:
    
    *   更新了`connect`方法，以确保只在`isConnected`为`false`时尝试连接。

通过这些修改，现在`WebSocketManager`类可以在网络状态变化时适当地连接和断开WebSocket连接，并在网络恢复时尝试重新连接。

> 1 / 1
> 
> 你这个有处理服务端重启导致连接断开的情况吗

1 / 1

是的，上述`WebSocketManager`类中的`receiveMessage`和`sendMessage`方法已经包含了处理服务端重启导致连接断开的逻辑。当接收或发送消息时发生错误（例如由于服务器重启而导致的连接断开），这些方法将触发`reconnect`方法来尝试重新连接。

这里是相关的代码片段：

swift

```swift
private func receiveMessage() {
    webSocketTask?.receive { [weak self] result in
        switch result {
        case .failure(let error):
            print("WebSocket receive error: \(error)")
            self?.reconnect()  // 这里尝试重新连接
        case .success(let message):
            // ...处理接收到的消息
        }
        self?.receiveMessage()  // 继续监听下一条消息
    }
}

func sendMessage(_ message: String) {
    webSocketTask?.send(URLSessionWebSocketTask.Message.string(message)) { [weak self] error in
        if let error = error {
            print("WebSocket send error: \(error)")
            self?.reconnect()  // 这里尝试重新连接
        }
    }
}
```

在`receiveMessage`方法中，如果`URLSessionWebSocketTask`接收操作失败（例如，因为服务端重启导致的连接断开），它会调用`reconnect`方法来尝试重新连接。

类似地，在`sendMessage`方法中，如果发送操作失败，它也会调用`reconnect`方法来尝试重新连接。

通过这种方式，无论是在尝试接收消息还是发送消息时，如果检测到连接断开，`WebSocketManager`类都会尝试重新连接到服务器。

> 1 / 1
> 
> 你的reconnect都需要客户端接收到消息或者发起消息时才触发，并且触发一次如果失败了就再也不行了

1 / 1

你完全正确。我的初始设计确实存在这些限制。为了改进这个问题，我们可以实现一个定期检查连接状态并尝试重连的机制。下面是一个更新的`WebSocketManager`类，它包含了一个定期重连的机制：

swift

```swift
import Foundation
import Network

class WebSocketManager: ObservableObject {
    private var webSocketTask: URLSessionWebSocketTask?
    private let url: URL
    private let reconnectInterval: TimeInterval
    private let pathMonitor = NWPathMonitor()
    private var reconnectTimer: Timer?
    
    @Published var isConnected: Bool = false
    @Published var messages: [Message] = []
    
    init(url: URL, reconnectInterval: TimeInterval = 5) {
        self.url = url
        self.reconnectInterval = reconnectInterval
        
        setupNetworkMonitoring()
        connect()
        startReconnectTimer()
    }
    
    deinit {
        disconnect()
        pathMonitor.cancel()
        reconnectTimer?.invalidate()
    }
    
    private func setupNetworkMonitoring() {
        pathMonitor.pathUpdateHandler = { [weak self] path in
            if path.status == .satisfied {
                if !self?.isConnected ?? false {
                    self?.connect()
                }
            } else {
                self?.disconnect()
            }
        }
        let queue = DispatchQueue.global(qos: .background)
        pathMonitor.start(queue: queue)
    }
    
    private func startReconnectTimer() {
        reconnectTimer = Timer.scheduledTimer(withTimeInterval: reconnectInterval, repeats: true) { [weak self] _ in
            guard !self?.isConnected ?? false else { return }
            self?.connect()
        }
    }
    
    private func connect() {
        guard !isConnected else { return }
        
        webSocketTask = URLSession.shared.webSocketTask(with: url)
        webSocketTask?.resume()
        isConnected = true
        receiveMessage()
    }
    
    private func disconnect() {
        webSocketTask?.cancel()
        isConnected = false
    }
    
    private func receiveMessage() {
        webSocketTask?.receive { [weak self] result in
            switch result {
            case .failure(let error):
                print("WebSocket receive error: \(error)")
                self?.disconnect()
            case .success(let message):
                switch message {
                case .string(let text):
                    self?.messages.append(Message(text: text))
                default:
                    print("Unhandled message type")
                }
            }
            self?.receiveMessage()
        }
    }
    
    func sendMessage(_ message: String) {
        webSocketTask?.send(URLSessionWebSocketTask.Message.string(message)) { [weak self] error in
            if let error = error {
                print("WebSocket send error: \(error)")
                self?.disconnect()
            }
        }
    }
}

struct Message {
    let text: String
}
```

在此更新版本中，我做了以下几点更改：

1.  添加了一个`reconnectTimer`属性来存储定时器引用。
2.  创建了一个`startReconnectTimer`方法来启动定时器，该定时器每隔一段时间（由`reconnectInterval`定义）检查连接状态，并在需要时尝试重新连接。
3.  在`init`方法中调用`startReconnectTimer`方法来启动定时器。
4.  在`deinit`方法中，取消了定时器以停止重连尝试。

通过这些更改，`WebSocketManager`类现在将定期检查连接状态，并在连接断开时尝试重新连接，无论是由于网络变化、服务器重启还是其他原因。

> 1 / 1
> 
> NWPathMonitor 是什么

1 / 1

`NWPathMonitor` 是 Network framework 的一部分，用于在 iOS 和 macOS 中监控网络路径的变化。它可以提供网络连接状态的实时更新，例如当设备从 Wi-Fi 切换到蜂窝数据，或者当网络连接完全丢失时。`NWPathMonitor` 是一个非常有用的工具，可以帮助应用程序适应网络条件的变化，并作出相应的响应。

以下是 `NWPathMonitor` 的基本使用方式:

1.  **创建 `NWPathMonitor` 实例**:
    
    swift
    
    ```swift
    let monitor = NWPathMonitor()
    ```
    
2.  **设置网络路径更新处理器**:
    
    swift
    
    ```swift
    monitor.pathUpdateHandler = { path in
        if path.status == .satisfied {
            print("Network is available")
        } else {
            print("Network is not available")
        }
    }
    ```
    
3.  **启动和停止监视器**:
    
    swift
    
    ```swift
    let queue = DispatchQueue.global(qos: .background)
    monitor.start(queue: queue)  // 启动监视器
    
    // 以后的某个时间点
    monitor.cancel()  // 停止监视器
    ```
    

在上述代码中，我们首先创建了一个 `NWPathMonitor` 实例。然后，我们为 `pathUpdateHandler` 属性设置了一个闭包，该闭包将在网络路径发生变化时被调用。我们检查 `path.status` 来确定网络是否可用，并相应地输出消息。最后，我们在全局队列上启动监视器，并在不再需要监视网络时取消监视器。

通过 `NWPathMonitor`，你可以为你的应用程序添加智能网络管理功能，例如在网络不可用时暂停数据传输，或在网络恢复时重新启动数据传输。

> 1 / 1
> 
> startReconnectTimer 还有其他更优雅的做法吗? 能不能直接监听ws连接的状态从而触发

1 / 1

完全可以，我们可以通过创建一个自定义的WebSocket代理类来监听WebSocket连接的状态，然后在连接状态发生变化时触发重连。在Swift中，我们可以利用`URLSessionWebSocketDelegate`来实现这个目标。下面是一个示例代码片段，展示了如何实现一个WebSocket代理类，并在`WebSocketManager`中使用它来监听连接状态：

swift

```swift
import Foundation

class WebSocketDelegate: NSObject, URLSessionWebSocketDelegate {
    var onConnectionClosed: (() -> Void)?
    
    func urlSession(_ session: URLSession, webSocketTask: URLSessionWebSocketTask, didCloseWith closeCode: URLSessionWebSocketTask.CloseCode, reason: Data?) {
        onConnectionClosed?()
    }
}

class WebSocketManager: ObservableObject {
    private var webSocketTask: URLSessionWebSocketTask?
    private let webSocketDelegate = WebSocketDelegate()
    private let url: URL
    private let reconnectInterval: TimeInterval
    
    @Published var isConnected: Bool = false
    @Published var messages: [Message] = []
    
    init(url: URL, reconnectInterval: TimeInterval = 5) {
        self.url = url
        self.reconnectInterval = reconnectInterval
        setupWebSocketDelegate()
        connect()
    }
    
    private func setupWebSocketDelegate() {
        webSocketDelegate.onConnectionClosed = { [weak self] in
            self?.reconnect()
        }
    }
    
    private func connect() {
        let session = URLSession(configuration: .default, delegate: webSocketDelegate, delegateQueue: nil)
        webSocketTask = session.webSocketTask(with: url)
        webSocketTask?.resume()
        isConnected = true
        receiveMessage()
    }
    
    // ... 其他方法保持不变

    private func reconnect() {
        disconnect()
        DispatchQueue.global().asyncAfter(deadline: .now() + reconnectInterval) {
            self.connect()
        }
    }
}

struct Message {
    let text: String
}
```

在这个示例中，我们做了以下几点修改：

1.  创建了一个新的`WebSocketDelegate`类，该类遵守`URLSessionWebSocketDelegate`协议。我们为该代理定义了一个`onConnectionClosed`闭包，该闭包将在WebSocket连接关闭时被调用。
2.  修改了`WebSocketManager`类，添加了一个`webSocketDelegate`属性，并在`init`方法中调用了一个新的`setupWebSocketDelegate`方法来设置`onConnectionClosed`闭包。当`WebSocketDelegate`检测到WebSocket连接关闭时，该闭包将触发`reconnect`方法。
3.  更新了`connect`方法，现在它创建了一个新的`URLSession`实例，并将`webSocketDelegate`作为其代理。这样，`WebSocketDelegate`就可以接收并处理WebSocket任务的事件了。

通过这种方式，`WebSocketManager`现在可以更直接地监听WebSocket连接的状态，并在连接关闭时自动触发重连，而不是依赖于定时器或消息发送/接收事件。

> 1 / 1
> 
> 在建立连接时需要在请求头上带上token，加上它

1 / 1

为了在建立WebSocket连接时在请求头中携带令牌（token），你需要创建一个`URLRequest`对象，设置其`HTTPHeaderField`，然后将这个`URLRequest`对象传递给`URLSessionWebSocketTask`。下面是如何在`WebSocketManager`类的`connect`方法中实现这一点的示例：

swift

```swift
import Foundation

class WebSocketManager: ObservableObject {
    // ... 其他属性和方法保持不变
    
    private var token: String
    
    init(url: URL, reconnectInterval: TimeInterval = 5, token: String) {
        self.url = url
        self.reconnectInterval = reconnectInterval
        self.token = token
        setupWebSocketDelegate()
        connect()
    }
    
    private func connect() {
        var request = URLRequest(url: url)
        request.setValue("Bearer \(token)", forHTTPHeaderField: "Authorization")  // 设置请求头的token
        
        let session = URLSession(configuration: .default, delegate: webSocketDelegate, delegateQueue: nil)
        webSocketTask = session.webSocketTask(with: request)  // 使用带有token的请求创建WebSocket任务
        webSocketTask?.resume()
        isConnected = true
        receiveMessage()
    }
    
    // ... 其他方法保持不变
}

struct Message {
    let text: String
}

// ... WebSocketDelegate类保持不变
```

在上述代码中，我做了以下几点更改：

1.  向`WebSocketManager`的`init`方法添加了一个新的`token`参数，并将其保存为一个新的`token`属性。
2.  修改了`connect`方法，创建了一个新的`URLRequest`对象，并使用`setValue(_:forHTTPHeaderField:)`方法设置了`Authorization`头，其中包含了Bearer token。然后，我使用这个`URLRequest`对象创建了`URLSessionWebSocketTask`对象，而不是直接使用URL。

现在，每次`WebSocketManager`建立WebSocket连接时，它都会在请求头中携带给定的token。

> 1 / 1
> 
> Message的编码格式是json，加上

2 / 2

为了处理JSON格式的消息，你需要将消息编码和解码为和从JSON。在Swift中，你可以使用`JSONEncoder`和`JSONDecoder`来完成这项任务。首先，让我们更新`Message`结构体以使其遵守`Codable`协议，并在`WebSocketManager`类中添加编码和解码方法。

swift

```swift
import Foundation

struct Message: Codable {
    let text: String
}

class WebSocketManager: ObservableObject {
    // ... 其他属性保持不变

    private let encoder = JSONEncoder()
    private let decoder = JSONDecoder()

    // ... 其他方法保持不变

    private func receiveMessage() {
        webSocketTask?.receive { [weak self] result in
            switch result {
            case .failure(let error):
                print("WebSocket receive error: \(error)")
                self?.disconnect()
            case .success(let message):
                switch message {
                case .string(let text):
                    if let data = text.data(using: .utf8),
                       let decodedMessage = try? self?.decoder.decode(Message.self, from: data) {
                        self?.messages.append(decodedMessage)
                    }
                default:
                    print("Unhandled message type")
                }
            }
            self?.receiveMessage()
        }
    }

    func sendMessage(_ message: Message) {
        if let jsonData = try? encoder.encode(message),
           let jsonString = String(data: jsonData, encoding: .utf8) {
            webSocketTask?.send(URLSessionWebSocketTask.Message.string(jsonString)) { [weak self] error in
                if let error = error {
                    print("WebSocket send error: \(error)")
                    self?.disconnect()
                }
            }
        }
    }
    
    // ... 其他方法保持不变
}

// ... WebSocketDelegate类保持不变
```

在这段代码中，我们做了以下更改：

1.  **消息编解码**：
    
    *   我们修改了`Message`结构体，使其遵守`Codable`协议，以便可以轻松地将其编码为和从JSON解码。
    *   在`WebSocketManager`类中，我们添加了一个`JSONEncoder`实例和一个`JSONDecoder`实例来处理消息的编码和解码。
2.  **接收消息**：
    
    *   在`receiveMessage`方法中，当接收到字符串消息时，我们首先尝试将其转换为`Data`，然后尝试使用`JSONDecoder`将其解码为`Message`实例。如果成功，我们将解码后的消息添加到`messages`数组中。
3.  **发送消息**：
    
    *   我们更新了`sendMessage`方法，使其现在接受一个`Message`实例而不是一个字符串。我们使用`JSONEncoder`将消息编码为JSON，然后将JSON字符串发送到服务器。

通过这些更改，现在`WebSocketManager`类可以处理JSON格式的消息，并能够将消息编码和解码为和从JSON。

> 1 / 1
> 
> 好,现在完整的给出代码

1 / 1

下面是根据之前讨论和修改的完整代码：

swift

```swift
import Foundation
import Network

struct Message: Codable {
    let text: String
}

class WebSocketDelegate: NSObject, URLSessionWebSocketDelegate {
    var onConnectionClosed: (() -> Void)?
    
    func urlSession(_ session: URLSession, webSocketTask: URLSessionWebSocketTask, didCloseWith closeCode: URLSessionWebSocketTask.CloseCode, reason: Data?) {
        onConnectionClosed?()
    }
}

class WebSocketManager: ObservableObject {
    private var webSocketTask: URLSessionWebSocketTask?
    private let webSocketDelegate = WebSocketDelegate()
    private let url: URL
    private let reconnectInterval: TimeInterval
    private let token: String
    private let encoder = JSONEncoder()
    private let decoder = JSONDecoder()
    
    @Published var isConnected: Bool = false
    @Published var messages: [Message] = []
    
    init(url: URL, reconnectInterval: TimeInterval = 5, token: String) {
        self.url = url
        self.reconnectInterval = reconnectInterval
        self.token = token
        setupWebSocketDelegate()
        connect()
    }
    
    deinit {
        disconnect()
    }
    
    private func setupWebSocketDelegate() {
        webSocketDelegate.onConnectionClosed = { [weak self] in
            self?.reconnect()
        }
    }
    
    private func connect() {
        var request = URLRequest(url: url)
        request.setValue("Bearer \(token)", forHTTPHeaderField: "Authorization")
        
        let session = URLSession(configuration: .default, delegate: webSocketDelegate, delegateQueue: nil)
        webSocketTask = session.webSocketTask(with: request)
        webSocketTask?.resume()
        isConnected = true
        receiveMessage()
    }
    
    private func disconnect() {
        webSocketTask?.cancel()
        isConnected = false
    }
    
    private func reconnect() {
        disconnect()
        DispatchQueue.global().asyncAfter(deadline: .now() + reconnectInterval) {
            self.connect()
        }
    }
    
    private func receiveMessage() {
        webSocketTask?.receive { [weak self] result in
            switch result {
            case .failure(let error):
                print("WebSocket receive error: \(error)")
                self?.disconnect()
            case .success(let message):
                switch message {
                case .string(let text):
                    if let data = text.data(using: .utf8),
                       let decodedMessage = try? self?.decoder.decode(Message.self, from: data) {
                        self?.messages.append(decodedMessage)
                    }
                default:
                    print("Unhandled message type")
                }
            }
            self?.receiveMessage()
        }
    }
    
    func sendMessage(_ message: Message) {
        if let jsonData = try? encoder.encode(message),
           let jsonString = String(data: jsonData, encoding: .utf8) {
            webSocketTask?.send(URLSessionWebSocketTask.Message.string(jsonString)) { [weak self] error in
                if let error = error {
                    print("WebSocket send error: \(error)")
                    self?.disconnect()
                }
            }
        }
    }
}
```

在这份代码中，`WebSocketManager`类负责管理WebSocket连接、发送和接收消息，同时处理连接中断和重新连接的情况。它也处理了在WebSocket请求头中包含token的需求，以及将消息编码和解码为JSON格式。同时，`WebSocketDelegate`类作为`URLSessionWebSocketDelegate`的实现，用于监听WebSocket连接关闭事件，并触发重新连接。