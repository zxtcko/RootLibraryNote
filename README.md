# RootLibraryNote
Notes on iOS basic library like Foundation, CoreAnimation
##一、CoreAnimation
[Official guide](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CoreAnimation_guide/Introduction/Introduction.html)
###Basics
*	Core Animation is a graphics rendering and animation infrastructure available on both iOS and OS X that you use to animate the views and other visual elements of your app.
*	 Core Animation sits beneath AppKit and UIKit and is integrated tightly into the view workflows of Cocoa and Cocoa Touch.

<img src = "IOSAnimationDemo/ca_architecture_2x.png" style = "width:300px;"/>

*	UIView和CALayer的区别：Layers are not a replacement for your app’s views—that is, you cannot create a visual interface based solely on layer objects. Layers provide infrastructure for your views. Specifically, layers make it easier and more efficient to draw and animate the contents of views and maintain high frame rates while doing so. However, there are many things that layers do not do. Layers do not handle events, draw content, participate in the responder chain, or do many other things. For this reason, every app must still have one or more views to handle those kinds of interactions.
	
	1.	CALayer继承自NSObject（无法响应事件）, UIView继承自UIResponser，NSObject（可以响应事件）
	2.	Layer提供绘画和动画的基本元素
	3.	UIView是iOS系统中界面元素的基础，所有界面元素都是继承自它。它本身完全是由CoreAnimation来实现。
	4.	一个UIView上可以由n个CALayer，每个CALayer显示一种东西，增强UIView的展现能力。 
	5.	In iOS, every view is backed by a corresponding layer object but in OS X you must decide which views should have layers.
<img src = "IOSAnimationDemo/basics_layer_rendering_2x.png" style = "width:600px;"/>

*	Layer主要分为三类：
	1.	数据层（model layer tree）是与app交互最多的，这一层的object存储动画的属性值。
	2.	展示层（presentation tree），数据层包含动画的目标属性值，而展示层包含展示在屏幕上动画的现有属性值，
	3.	渲染层（render tree），在渲染层的Object表现真实的动画，并且是core animation的私有变量
	
<img src = "https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CoreAnimation_guide/Art/sublayer_hierarchies_2x.png" style = "width:600px;"/>
	
	