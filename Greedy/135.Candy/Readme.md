### 135.Candy

此题是贪心法的经典题。所谓贪心法，并没有定式，是指可以人工找出最优的策略，当然这种策略必须可以直观或者严谨地证明。

设置candy数组的初始值为1。

先从左往右扫一遍，如果右边的rating高于左边，则设置右边的candy要比左边的多一颗。扫完之后就保证了所有的“右边大于左边”的情况都得到了满足。

再从右往左扫一遍，如果左边的rating高于右边但糖果不比右边多，则设置左边的candy比右边多一颗。注意，这个操作并没有打破之前“右边大于左边”操作的结果。扫完之后就保证了所有的“左边大于右边”的情况都得到了满足。

扫完两边后，“右边大于左边”、“左边大于右边”都得到了满足，那么就是符合题意的安排。
