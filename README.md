# RootLibraryNote
Notes on iOS basic library like Foundation, CoreAnimation
##一、CoreAnimation
[Official guide](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CoreAnimation_guide/Introduction/Introduction.html)
###Basics
*	Core Animation is a graphics rendering and animation infrastructure available on both iOS and OS X that you use to animate the views and other visual elements of your app.
*	 Core Animation sits beneath AppKit and UIKit and is integrated tightly into the view workflows of Cocoa and Cocoa Touch.

<img src = "IOSAnimationDemo-master/ca_architecture_2x.png" style = "width:300px;"/>

*	UIView和CALayer的区别：Layers are not a replacement for your app’s views—that is, you cannot create a visual interface based solely on layer objects. Layers provide infrastructure for your views. Specifically, layers make it easier and more efficient to draw and animate the contents of views and maintain high frame rates while doing so. However, there are many things that layers do not do. Layers do not handle events, draw content, participate in the responder chain, or do many other things. For this reason, every app must still have one or more views to handle those kinds of interactions.
	
	1.	CALayer继承自NSObject（无法响应事件）, UIView继承自UIResponser，NSObject（可以响应事件）
	2.	Layer提供绘画和动画的基本元素
	3.	UIView是iOS系统中界面元素的基础，所有界面元素都是继承自它。它本身完全是由CoreAnimation来实现。
	4.	一个UIView上可以由n个CALayer，每个CALayer显示一种东西，增强UIView的展现能力。 
	5.	In iOS, every view is backed by a corresponding layer object but in OS X you must decide which views should have layers.
<img src = "https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CoreAnimation_guide/Art/basics_layer_rendering_2x.png" style = "width:600px;"/>

*	Layer主要分为三类：
	1.	数据层（model layer tree）是与app交互最多的，这一层的object存储动画的属性值。
	2.	展示层（presentation tree），数据层包含动画的目标属性值，而展示层包含展示在屏幕上动画的现有属性值，
	3.	渲染层（render tree），在渲染层的Object表现真实的动画，并且是core animation的私有变量
	
<img src = "https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CoreAnimation_guide/Art/sublayer_hierarchies_2x.png" style = "width:600px;"/>
	

	
	
*	CALayer的子类
<table class="graybox" border="0" cellspacing="0" cellpadding="5">
  <caption class="tablecaption">
    <strong class="caption_number"></strong>&nbsp;&nbsp;
    CALayer subclasses and their uses</caption>
  <tbody>
    <tr>
      <th scope="col" class="TableHeading_TableRow_TableCell">
        <p>Class</p>
      </th>
      <th scope="col" class="TableHeading_TableRow_TableCell">
        <p>Usage</p>
      </th>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CAEmitterLayer</code>
        </p>
      </td>
      <td>
        <p>Used to implement a Core Animation–based particle emitter system. The emitter layer object controls the generation of the particles and their origin.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CAGradientLayer</code>
        </p>
      </td>
      <td>
        <p>Used to draw a color gradient that fills the shape of the layer (within the bounds of any rounded corners).</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CAMetalLayer</code>
        </p>
      </td>
      <td>
        <p>Used to set up and vend drawable textures for rendering layer content using Metal.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CAEAGLLayer</code>/
          <code>
            <!--a target="_self" -->CAOpenGLLayer
            <!--/a--></code></p>
      </td>
      <td>
        <p>Used to set up the backing store and context for rendering layer content using OpenGL ES (iOS) or OpenGL (OS&nbsp;X).</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CAReplicatorLayer</code>
        </p>
      </td>
      <td>
        <p>Used when you want to make copies of one or more sublayers automatically. The replicator makes the copies for you and uses the properties you specify to alter the appearance or attributes of the copies.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CAScrollLayer</code>
        </p>
      </td>
      <td>
        <p>Used to manage a large scrollable area composed of multiple sublayers.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CAShapeLayer</code>
        </p>
      </td>
      <td>
        <p>Used to draw a cubic Bezier spline. Shape layers are advantageous for drawing path-based shapes because they always result in a crisp path, as opposed to a path you draw into a layer’s backing store, which would not look as good when scaled. However, the crisp results do involve rendering the shape on the main thread and caching the results.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CATextLayer</code>
        </p>
      </td>
      <td>
        <p>Used to render a plain or attributed string of text.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CATiledLayer</code>
        </p>
      </td>
      <td>
        <p>Used to manage a large image that can be divided into smaller tiles and rendered individually with support for zooming in and out of the content.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            CATransformLayer</code>
        </p>
      </td>
      <td>
        <p>Used to render a true 3D layer hierarchy, rather than the flattened layer hierarchy implemented by other layer classes.</p>
      </td>
    </tr>
    <tr>
      <td scope="row">
        <p>
          <code>
            <!--a target="_self" -->QCCompositionLayer
            <!--/a--></code></p>
      </td>
      <td>
        <p>Used to render a Quartz Composer composition. (OS&nbsp;X only)</p>
      </td>
    </tr>
  </tbody>
</table>

*	BackgroundColor, Contents, Border的关系

<img src = "https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/CoreAnimation_guide/Art/layer_border_background_2x.png" style = "width:300px;"/>


##二、Foundation
[教程](http://swifter.tips/foundation-framework/)
###Basic
Swift 的基本类型都可以无缝转换到 Foundation 框架中的对应类型

这个转换不仅是自动的，而且是双向的，但是转换的结果会更倾向于使用 Swift 类型。
只要你不写明类型是需要 NS 开头的类型的时候，你都会得到一个 Swift 类型。这类转换有下面的对应关系：

*	String - NSString
*	Int, Float, Double, Bool 以及其他与数字有关的类型 - NSNumber
*	Array - NSArray
*	Dictionary - NSDictionary
