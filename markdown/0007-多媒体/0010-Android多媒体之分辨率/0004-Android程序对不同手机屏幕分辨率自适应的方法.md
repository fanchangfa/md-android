相信各位Android开发爱好者都知道，由于OEM之间的竞争，各种Android操作系统的手机简直就是琳琅满目，屏幕分辨率的差异可想而知。目前比较主流的有WVGA=800x480，HVGA=480x320，另外的还有QVGA=320x240。当然还有魅族M9的DVGA=960x640，还有蛋疼的摩托罗拉的FWVGA=854x480。 
那么，如何让你的程序可以在不同分辨率的手机上“健康”的跑动呢？
其实，在你layout的xml文件中，编写的时候是不是用了许多的padding呢？如果是，那你就蛋疼了。因为这样的布局永远是无法适应所有手机屏幕的。正确的做法应该是使用weight属性。
过程很简单：首先，将你控件的layout中的width、height设置为fill-parent，不要使用wrap——content。因为wrap-content的大小是不固定的。而weight（权重）这个属性很好的解决了这个问题。
当包裹在控件外面的Layout的width、height属性都设置为fill-parent时，可以利用weight的反比特性。即如果控件A设置weight为9，控件B设置weight为20，那么A所占的空间为20/（9+20），B所占的空间为9/（9+20）。这样的反比属性对任何分辨率下的手机都是合适的。
当然，字体就不行了。那怎么保证字体能够跟布局一样能够自适应呢？
呵呵，很简单，就是在你的res文件夹中创建一个文件夹，叫做values-320x240。其中320x240是你手机屏幕的分辨率，根据你手机屏幕的情况做不同的命名，例如values-800x480。在该文件夹下创建一个dimens.xml文件，定义各种字体的大小。那么系统就会自动根据你手机屏幕的分辨率去调用响应的文件夹。
另外，值得提醒的是，记得在你默认的values文件下的dimens.xml文件中也要写上相应的字体大小哦，因为当系统无法认识你手机屏幕大小的时候，它会自动去找你默认文件中的东西，没有写的话程序会崩溃。
这样编写出来的xml文件就是对所有手机屏幕自适应的哦亲。