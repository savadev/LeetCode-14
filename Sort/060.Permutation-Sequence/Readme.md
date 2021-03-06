### 060.Permutation-Sequence

首先，创建一个集合，存储数字选项1,2,3,4,5,6,7,8,9。

假设第一个位置的数字是1，那么总共有多少个这样的全排列呢？显然就是考虑第2\~N位上用数字2~N去做全排列，就是(N-1)\!个可能。同理，第一个位置如果是2的话，那么也有(N-1)\!个可能；第一个数字是3，同理也有(N-1)\!个可能……

所以，用k除以(N-1)!得到的结果，就可以确定第一个位置的数字。例如：4xxxxxxxx符合要求的全排列共有```(N-1)!*4```个，形如5xxxxxxxx符合要求的全排列共有```(N-1)!*5```个，假设k除以```(N-1)!```的结果大于4且小于5，那么说明所需要的第k大的全排列一定在这两者之间。故它的第一个位置的数字一定是5。这里需要注意一个技巧，我们预先将k减去1，这样我们其实寻找的是0-index标准下的第k个全排列。这样```a=k/(N-1)!```无论是否整除，a的值就意味着我们需要在digit（剩余）的集合里面找第a个元素（同样是0-index）。

同理，接下来考虑第二个位置的数字。注意到刚才已经排除了形如4xxxxxxxx的排列，剩下来我们其实寻找的就是以5开头的、第```k-(N-1)!*4```个全排列。所以我们更新```k-=(N-1)!*4```，此时的任务演变成了：求由N-1个元素组成的全排列里面第k个是多少。我们可以重复上面的方法，通过查看```k/(N-2)!```的结果来判定第二位上的数字是什么。注意，每确定了一个数字，就需要从digit集合中删除那一个避免重复使用。

依次类推，就可以确定所有位置上的数字。值得指出的是，当n降为1的时候，此时的k一定会是零。
