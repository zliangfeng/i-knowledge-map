# z-index

## refs

- <https://cloud.tencent.com/developer/article/1679221>

## Content

- 如果把 html 比作 room，则`层叠上下文`(the stacking context)则是一张张桌子
  - 桌子A覆盖了桌子B，意味着桌子A覆盖了桌子B上的所有物件；
- `层叠顺序`(从低到高)
  1. 背景和边框 ：形成层叠上下文的元素的背景和边框，它是整个上下文中层叠等级最低的。
  2. Z-Index 为负数 ：设置了 z-index 为负数的子元素以及由它所产生的层叠上下文
  3. 块级盒模型：位于正常文档流中的、块级的、非定位的子元素
  4. 浮动盒模型 ：浮动的、非定位的子元素
  5. 内联盒模型 ：位于正常文档流中的、内联的、非定位的子元素
  6. Z-index 为 0：设置了 z-index 为 0 的、定位的子元素以及由它所产生的层叠上下文
  7. Z-Index 为正数 ：设置了 z-index 为正数的、定位的子元素以及由它所产生的层叠上下文，它是整个上下文中层叠等级最高的
