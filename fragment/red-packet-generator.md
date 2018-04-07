## 简单红包生成器

> 抢红包的时候思考了一下红包算法的实现，自己尝试写了一个很简单的算法。

<br>
#### 环境说明
Macos  
g++

```c++
/*
 * @author 王镇佳 <wzjfloor@163.com>
 * @description 生成随机红包的c++实现
 * @date 2017.1.30
 */
#include <iostream>
#include <cstdlib>
#include <algorithm>

#define MAX_ARRAY_LEN 100000

using std::cout;
using std::cin;
using std::endl;

// sort比较函数
bool cmp(double, double);
void generateRandomRedPacket(int, double);

// 全局堆存储变量 Mac最大可支持千万级别, 默认十万级
double storeArr[MAX_ARRAY_LEN] = { 0 };
double randomArr[MAX_ARRAY_LEN] = { 0 };

int main() {
  int redPacketNum = 0;
  double totalNum = 0;

  while(1) {
    cout << "请输入红包数目:" << endl;
    cin >> redPacketNum;
    cout << "请输入红包总额:" << endl;
    cin >> totalNum;

    generateRandomRedPacket(redPacketNum, totalNum);
  }

  return 0;
}

bool cmp(double a, double b) {
  return a < b;
}

void generateRandomRedPacket(int redPacketNum, double totalNum) {
  srand((unsigned)time(NULL));

  randomArr[0] = 0;
  for (int i = 1; i < redPacketNum; i++) {
    randomArr[i] = rand() * totalNum / (double)(RAND_MAX);
    // 取小数点后两位
    randomArr[i] = (int)(randomArr[i] * 100) / 100.0;
  }
  randomArr[redPacketNum] = totalNum;

  std::sort(randomArr, randomArr + redPacketNum, cmp);

  // 计算最佳手气
  double max = 0;
  // 隔板插入  取区间作为红包金额
  for (int i = 0; i < redPacketNum; i++) {
    storeArr[i] = randomArr[i + 1] - randomArr[i];
    max = storeArr[i] > max ? storeArr[i] : max;
    cout << "第" << i + 1 << "个红包值" << storeArr[i] << endl;
  }
  cout << endl << "最佳手气" << max << endl;
}
```
