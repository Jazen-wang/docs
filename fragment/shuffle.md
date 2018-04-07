## Fisher–Yates shuffle 洗牌算法

> 描述：一个有限集合生成一个随机排列的算法（数组随机排序）。这个算法生成的随机排列是等概率的。同时这个算法非常高效。

```javascript
/**
 * Fisher–Yates shuffle
 */
Array.prototype.shuffle = function() {
  var input = this;

  for (var i = input.length-1; i >=0; i--) {
    var randomIndex = Math.floor(Math.random()*(i+1));
    var itemAtIndex = input[randomIndex];

    input[randomIndex] = input[i];
    input[i] = itemAtIndex;
  }
  return input;
}
```

| 随机数取值范围 | 随机数  | 原始数据            | 结果            |
| ------- | ---- | --------------- | ------------- |
|         |      | 1 2 3 4 5 6 7 8 |               |
| 1-8     | 6    | 1 2 3 4 5 7 8   | 6             |
| 1-7     | 2    | 1 7 3 4 5 8     | 2 6           |
| 1–6     | 6    | 1 7 3 4 5       | 8 2 6         |
| 1–5     | 1    | 5 7 3 4         | 1 8 2 6       |
| 1–4     | 3    | 5 7 4           | 3 1 8 2 6     |
| 1–3     | 3    | 5 7             | 4 3 1 8 2 6   |
| 1–2     | 1    | 7               | 5 4 3 1 8 2 6 |





Fisher–Yates shuffle 的原始版本，最初描述在 1938 年的 Ronald Fisher（上图） 和 Frank Yates 写的书中，书名为《Statistical tables for biological, agricultural and medical research》。他们使用纸和笔去描述了这个算法，并使用了一个随机数表来提供随机数。它给出了 1 到 N 的数字的的随机排列，具体步骤如下：

1. 写下从 1 到 N 的数字
2. 取一个从 1 到剩下的数字（包括这个数字）的随机数 k
3. 从低位开始，得到第 k 个数字（这个数字还没有被取出），把它写在独立的一个列表的最后一位
4. 重复第 2 步，直到所有的数字都被取出
5. 第 3 步写出的这个序列，现在就是原始数字的随机排列

已经证明如果第 2 步取出的数字是真随机的，那么最后得到的排序一定也是。