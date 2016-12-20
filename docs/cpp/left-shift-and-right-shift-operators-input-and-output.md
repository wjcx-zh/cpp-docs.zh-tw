---
title: "左移和右移運算子 (&gt;&gt; 和 &lt;&lt;) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "<<"
  - ">>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<< 運算子, 使用特定物件"
  - ">> 運算子"
  - "位元移位運算子"
  - "左移運算子"
  - "運算子 [C++], 移位"
  - "向右移位運算子"
  - "移位運算子"
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 左移和右移運算子 (&gt;&gt; 和 &lt;&lt;)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

位元移位運算子是右移位運算子 \(`>>`\)，會將 `shift_expression` 的位元向右移，另外還有左移位運算子 \(`<<`\)，會將 `shift_expression` 的位元向左移。  <sup>1</sup>  
  
## 語法  
  
```  
  
        shift-expression << additive-expression  
shift-expression >> additive-expression  
```  
  
## 備註  
  
> [!IMPORTANT]
>  下列說明和範例適用於 x86 和 x64 架構的 Windows。  左移位和右移位運算子在 Windows RT for ARM 裝置的實作非常不同。  如需詳細資訊，請參閱 [Hello ARM](http://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) \(英文\) 部落格文章中的＜移位運算子＞一節。  
  
## 左移位  
 左移位運算子會使 `shift-expression` 中的位元向左移動 `additive-expression` 所指定的位置數目。  移位作業空出的位元位置以零填補。  左移是邏輯移位 \(會捨棄移出結尾的位元，包括正負號位元\)。  如需此類位元移位的詳細資訊，請參閱[位元移位](http://en.wikipedia.org/wiki/Bitwise_shift) \(英文\)。  
  
 下列範例示範使用不帶正負號數字的左移位作業。  此範例以值代表 bitset 說明位元的行為。  如需詳細資訊，請參閱 [bitset 類別](../standard-library/bitset-class.md)。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short1 = 4;      
    bitset<16> bitset1{short1};   // the bitset representation of 4  
    cout << bitset1 << endl;  // 0000000000000100  
  
    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;  // 0000000000001000  
  
    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16  
    bitset<16> bitset3{short3};  
    cout << bitset3 << endl;  // 0000000000010000  
}  
  
```  
  
 如果將帶正負號的數字左移，以影響正負號位元，結果會是未定義。  下列範例示範在 Visual C\+\+ 中將一個 1 位元左移到帶正負號位元位置時的情況。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 16384;      
    bitset<16> bitset1{short2};  
    cout << bitset1 << endl;  // 0100000000000000   
  
    short short3 = short1 << 1;  
    bitset<16> bitset3{short3};  // 16384 left-shifted by 1 = -32768  
    cout << bitset3 << endl;  // 100000000000000  
  
    short short4 = short1 << 14;  
    bitset<16> bitset4{short4};  // 4 left-shifted by 14 = 0  
    cout << bitset4 << endl;  // 000000000000000    
}  
```  
  
## 右移位  
 右移位運算子會使 `shift-expression` 中的位元模式向右移動 `additive-expression` 所指定的位置數目。  若是不帶正負號的數字，移位作業空出的位元位置以零填補。  若是帶正負號的數字，會使用正負號位元填補空出的位元位置。  換句話說，如果是正數就會使用 0，負數則使用 1。  
  
> [!IMPORTANT]
>  將帶正負號負數向右移的結果與實作相關。  雖然 Visual C\+\+ 使用正負號位元填補空出來的位元位置，但不保證其他實作也會如此。  
  
 此範例示範使用不帶正負號數字的右移位作業：  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short11 = 1024;  
    bitset<16> bitset11{short11};  
    cout << bitset11 << endl;     // 0000010000000000  
  
    unsigned short short12 = short11 >> 1;  // 512  
    bitset<16> bitset12{short12};  
    cout << bitset12 << endl;     // 0000001000000000  
  
    unsigned short short13 = short11 >> 10;  // 1  
    bitset<16> bitset13{short13};  
    cout << bitset13 << endl;     // 0000000000000001  
  
    unsigned short short14 = short11 >> 11;  // 0  
    bitset<16> bitset14{short14};  
    cout << bitset14 << endl;     // 0000000000000000}  
}  
```  
  
 下一個範例示範使用正號數字的右移位作業。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 1024;  
    bitset<16> bitset1{short1};  
    cout << bitset1 << endl;     // 0000010000000000  
  
    short short2 = short1 >> 1;  // 512  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;     // 0000001000000000  
  
    short short3 = short1 >> 11;  // 0  
    bitset<16> bitset3{short3};     
    cout << bitset3 << endl;     // 0000000000000000  
}  
```  
  
 下一個範例示範使用帶負號整數右移位作業。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short neg1 = -16;  
    bitset<16> bn1{neg1};  
    cout << bn1 << endl;  // 1111111111110000  
  
    short neg2 = neg1 >> 1; // -8  
    bitset<16> bn2{neg2};  
    cout << bn2 << endl;  // 1111111111111000  
  
    short neg3 = neg1 >> 2; // -4  
    bitset<16> bn3{neg3};  
    cout << bn3 << endl;  // 1111111111111100  
  
    short neg4 = neg1 >> 4; // -1  
    bitset<16> bn4{neg4};      
    cout << bn4 << endl;  // 1111111111111111  
  
    short neg5 = neg1 >> 5; // -1   
    bitset<16> bn5{neg5};      
    cout << bn5 << endl;  // 1111111111111111  
}  
```  
  
## 移位和提升  
 移位運算子兩邊的運算式都必須是整數類型。  整數提升會根據[整數提升](../misc/integral-promotions.md)中描述的規則執行。  結果的類型與提升之 `shift-expression` 的類型相同。  
  
 下列範例會將屬於 `char` 類型的變數提升為 `int`。  
  
```cpp  
#include <iostream>  
#include <typeinfo>  
  
using namespace std;  
  
int main() {  
    char char1 = 'a';  
  
    auto promoted1 = char1 << 1;  // 194  
    cout << typeid(promoted1).name() << endl;  // int  
  
    auto promoted2 = char1 << 10;  // 99328  
    cout << typeid(promoted2).name() << endl;   // int  
}  
```  
  
## 其他詳細資料  
 如果 `additive-expression` 是負數或 `additive-expression` 大於或等於 \(已提升\) `shift-expression` 中的位元數，則移位作業的結果會是未定義。  如果 `additive-expression` 是 0，不會執行任何移位作業。  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned int int1 = 4;  
    bitset<32> b1{int1};  
    cout << b1 << endl;    // 00000000000000000000000000000100  
  
    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior  
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior  
  
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int6 = int1 << 0;  
    bitset<32> b6{int6};  
    cout << b6 << endl;    // 00000000000000000000000000000100 (no change)}  
}  
```  
  
## 註腳  
 1 以下說明 C\+\+ ISO 規格 \(INCITS\/ISO\/IEC 14882\-2011\[2012\]\) 第 5.8.2 和 5.8.3 節的移位運算子。  
  
 `E1 << E2` 的值是向左移位 `E1` 的 `E2` 位元位置；空出的位元會以零填補。  如果 `E1` 具有不帶正負號的類型，結果的值會是 `E1 × 2`<sup>E2</sup>，比結果類型中可顯示的最大值少一個餘數。  否則，如果 `E1` 的類型帶正負號，且具有非負數值，且結果類型之對應不帶正負號類型可以顯示 `E1 × 2`<sup>E2</sup>，則轉換為結果類型的值即為結果值，否則該行為即為未定義。  
  
 `E1 >> E2` 的值是 `E1` 向右移位 `E2` 個位元位置。  如果 `E1` 的類型不帶正負號，或者 `E1` 的類型帶正負號且具有非負數值，則結果的值會是 `E1/2`<sup>E2</sup> 商數的整數部分。  如果 `E1` 的類型帶正負號，且具有負數值，結果產生的值由實作決定。  
  
## 請參閱  
 [具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)