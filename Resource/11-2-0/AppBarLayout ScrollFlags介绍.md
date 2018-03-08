### AppBarLayout ScrollFlags介绍

```
app:layout_scrollFlags="scroll|exitUntilCollapsed|snap"
```



#### scroll

> The view will be scroll in direct relation to scroll events. This flag needs to be set for any of the other flags to take effect. If any sibling views before this one do not have this flag, then this value has no effect.

需要响应滚动必须设置的标示！Child View 随着滚动事件滚出或滚进屏幕。

1. 想要响应其他的标示，必须有这个标示存在才行
2. 当前Child View前面的任何其他Child View没有设置这个值，那么这个Child View的设置将失去作用；因为滚动会被挡住。



#### enterAlways

> When entering (scrolling on screen) the view will scroll on any downwards scroll event, regardless of whether the scrolling view is also scrolling. This is commonly referred to as the 'quick return' pattern.

优先响应滚动模式。其实是向下滚动时Scrolling View（RecyclerView）和Child View（Appbar的子View）之间的滚动优先级问题。

* 仅仅设置scroll标示：发生向下滚动事件时，前者优先滚动Scrolling View（RecyclerView），当滚动到底的时候，才响应Appbar的滚动（一般是拉出操作）。
* scroll | enterAlways：优先滚动Child View，当优先滚动的一方已经全部滚进屏幕之后，另一方Scrolling View（RecyclerView）才开始滚动。



#### enterAlwaysCollapsed

> An additional flag for 'enterAlways' which modifies the returning view to only initially scroll back to it's collapsed height. Once the scrolling view has reached the end of it's scroll range, the remainder of this view will be scrolled into view. The collapsed height is defined by the view's minimum height.

enterAlways的附加值。滚动时优先响应Child View的滚动，但是仅仅只滚动最小高度；随后响应Scrolling View（RecyclerView）的滚动，当RecyclerView到达边界时，Child View再向下滚动，直至显示完全。



#### exitUntilCollapsed

> When exiting (scrolling off screen) the view will be scrolled until it is 'collapsed'. The collapsed height is defined by the view's minimum height.

exit是退出，与enter相反；向上滚动时为退出，向下就是进入。目标是Appbar控件。

* 这里也涉及到最小高度。
* 发生向上滚动事件时，Child View向上滚动退出直至最小高度，然后Scrolling View开始滚动。
* Child View不会完全退出屏幕，保持最小高度。



#### snap

> Upon a scroll ending, if the view is only partially visible then it will be snapped and scrolled to it's closest edge. For example, if the view only has it's bottom 25% displayed, it will be scrolled off screen completely. Conversely, if it's bottom 75% is visible then it will be scrolled fully into view.

“咬住”！！！简单说就是Child View滚动比例的一个吸附效果。

* Child View不会存在局部显示的情况（只会完全显示，不显示，最小高度显示）
* 响应滚动Child View移动了部分高度，当我们松开手指时，Child View要么向上全部滚出屏幕（或者最小高度），要么向下全部滚进屏幕，类似ViewPager的左右滑动，不会有中间停留的情况。

