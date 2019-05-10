---
title: 左的移和右移運算子 (&gt; &gt;並&lt; &lt;)
ms.date: 08/13/2018
f1_keywords:
- <<
- '>>'
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
ms.openlocfilehash: fd048bedc45b14bdc7b83120ad039296b54aa850
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222057"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>左的移和右移運算子 (&gt; &gt;並&lt; &lt;)

位元移位運算子是右移位運算子 (**&gt;&gt;**)，會將位元*shift 運算式*右側和左移運算子 (**&lt; &lt;**)，會將位元*shift 運算式*左邊。 <sup>1</sup>

## <a name="syntax"></a>語法

> *shift-expression* `<<` *additive-expression*
> *shift-expression* `>>` *additive-expression*

## <a name="remarks"></a>備註

> [!IMPORTANT]
> 下列說明和範例上皆有效 Windows 適用於 x86 和 x64 架構。 左移和右移運算子的實作很大的差異在 Windows 上適用於 ARM 裝置。 如需詳細資訊，請參閱的 < 移位運算子 > 一節[Hello ARM](https://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx)部落格文章。

## <a name="left-shifts"></a>左移位

左移位運算子會導致中的位元*shift 運算式*所指定的位置數目，向左移位*加法運算式*。 移位作業空出的位元位置以零填補。 左移是邏輯移位 (會捨棄移出結尾的位元，包括正負號位元)。 如需此類位元移位的詳細資訊，請參閱[位元移位](https://en.wikipedia.org/wiki/Bitwise_shift)。

下列範例示範使用不帶正負號數字的左移位作業。 此範例以值代表 bitset 說明位元的行為。 如需詳細資訊，請參閱 < [bitset 類別](../standard-library/bitset-class.md)。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short1 = 4;
    bitset<16> bitset1{short1};   // the bitset representation of 4
    cout << bitset1 << endl;  // 0b00000000'00000100

    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8
    bitset<16> bitset2{short2};
    cout << bitset2 << endl;  // 0b00000000'00001000

    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16
    bitset<16> bitset3{short3};
    cout << bitset3 << endl;  // 0b00000000'00010000
}
```

如果將帶正負號的數字左移，以影響正負號位元，結果會是未定義。 下列範例示範當 1 的位元的正負號位元位置向左移位時，會發生什麼事。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 16384;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;  // 0b01000000'00000000

    short short3 = short1 << 1;
    bitset<16> bitset3(short3);  // 16384 left-shifted by 1 = -32768
    cout << bitset3 << endl;  // 0b10000000'00000000

    short short4 = short1 << 14;
    bitset<16> bitset4(short4);  // 4 left-shifted by 14 = 0
    cout << bitset4 << endl;  // 0b00000000'00000000
}
```

## <a name="right-shifts"></a>右移位

向右移位運算子會導致中的位元模式*shift 運算式*所指定的位置數目，向右移位*加法運算式*。 若是不帶正負號的數字，移位作業空出的位元位置以零填補。 若是帶正負號的數字，會使用正負號位元填補空出的位元位置。 換句話說，如果是正數就會使用 0，負數則使用 1。

> [!IMPORTANT]
> 將帶正負號負數向右移的結果與實作相關。 雖然 MicrosoftC++編譯器用來填滿空出的位元位置的正負號位元，則無法保證，其他實作也會如此。

此範例示範使用不帶正負號數字的右移位作業：

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short11 = 1024;
    bitset<16> bitset11{short11};
    cout << bitset11 << endl;     // 0b00000100'00000000

    unsigned short short12 = short11 >> 1;  // 512
    bitset<16> bitset12{short12};
    cout << bitset12 << endl;     // 0b00000010'00000000

    unsigned short short13 = short11 >> 10;  // 1
    bitset<16> bitset13{short13};
    cout << bitset13 << endl;     // 0b00000000'00000001

    unsigned short short14 = short11 >> 11;  // 0
    bitset<16> bitset14{short14};
    cout << bitset14 << endl;     // 0b00000000'00000000
}
```

下一個範例示範使用正號數字的右移位作業。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 1024;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;     // 0b00000100'00000000

    short short2 = short1 >> 1;  // 512
    bitset<16> bitset2(short2);
    cout << bitset2 << endl;     // 0b00000010'00000000

    short short3 = short1 >> 11;  // 0
    bitset<16> bitset3(short3);
    cout << bitset3 << endl;     // 0b00000000'00000000
}
```

下一個範例示範使用帶負號整數右移位作業。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short neg1 = -16;
    bitset<16> bn1(neg1);
    cout << bn1 << endl;  // 0b11111111'11110000

    short neg2 = neg1 >> 1; // -8
    bitset<16> bn2(neg2);
    cout << bn2 << endl;  // 0b11111111'11111000

    short neg3 = neg1 >> 2; // -4
    bitset<16> bn3(neg3);
    cout << bn3 << endl;  // 0b11111111'11111100

    short neg4 = neg1 >> 4; // -1
    bitset<16> bn4(neg4);
    cout << bn4 << endl;  // 0b11111111'11111111

    short neg5 = neg1 >> 5; // -1
    bitset<16> bn5(neg5);
    cout << bn5 << endl;  // 0b11111111'11111111
}
```

## <a name="shifts-and-promotions"></a>移位和提升

移位運算子兩邊的運算式都必須是整數類型。 根據規則中所述執行整數提升[標準轉換](standard-conversions.md)。 結果的型別是相同的類型與提升*shift 運算式*。

在下列範例中，類型的變數**char**升級到**int**。

```cpp
#include <iostream>
#include <typeinfo>

using namespace std;

int main() {
    char char1 = 'a';

    auto promoted1 = char1 << 1;   // 194
    cout << typeid(promoted1).name() << endl;  // int

    auto promoted2 = char1 << 10;  // 99328
    cout << typeid(promoted2).name() << endl;  // int
}
```

## <a name="additional-details"></a>其他詳細資料

如果移位運算的結果是未定義*加法運算式*為負數或者*加法運算式*大於或等於 （已提升） 中的位元數*shift 運算式*。 如果執行任何移位作業*加法運算式*為 0。

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned int int1 = 4;
    bitset<32> b1{int1};
    cout << b1 << endl;    // 0b00000000'00000000'00000000'00000100

    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int6 = int1 << 0;
    bitset<32> b6{int6};
    cout << b6 << endl;    // 0b00000000'00000000'00000000'00000100 (no change)
}
```

## <a name="footnotes"></a>註腳

<sup>1</sup>如下的 c++11 ISO 規格 （INCITS/ISO/IEC 14882-2011[2012])，5.8.2 和 5.8.3 節的移位運算子描述

`E1 << E2` 的值是向左移位 `E1` 的 `E2` 位元位置；空出的位元會以零填補。 如果`E1`具有不帶正負號的類型，結果的值是**E1 × 2**<sup>**E2**</sup>，少比結果類型中可顯示的最大值的一個餘數。 否則，如果`E1`帶正負號的類型且具有非負數值，並**E1 × 2**<sup>**E2** </sup>就對應不帶正負號類型的結果型別中可顯示值，轉換為結果型別是所產生的值;否則行為未定義。

`E1 >> E2` 的值是 `E1` 向右移位 `E2` 個位元位置。 如果`E1`具有不帶正負號的類型或是`E1`具有帶正負號的類型，而且具有非負數值，結果的值是不可或缺的一部分的商數**E1/2**<sup>**E2** </sup>. 如果 `E1` 的類型帶正負號，且具有負數值，結果產生的值由實作決定。

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
