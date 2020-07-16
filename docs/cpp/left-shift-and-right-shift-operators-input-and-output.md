---
title: 左移和右移運算子（ &gt; &gt; 和 &lt; &lt; ）
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
ms.openlocfilehash: 7cde299d305219f2bd0e53a9f19c2ca35a8c7b69
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404766"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>左移和右移運算子（ &gt; &gt; 和 &lt; &lt; ）

位移位運算子是右移運算子（ **&gt;&gt;** ），它會將*shift 運算式*的位向右移動，而左移運算子（）則會 **&lt;&lt;** 將*shift 運算式*的位向左移動。 <sup>1</sup>

## <a name="syntax"></a>語法

> *shift 運算式* `<<`*加法類運算式*\
> *shift-expression* `>>` *additive-expression*

## <a name="remarks"></a>備註

> [!IMPORTANT]
> 下列說明和範例在適用于 x86 和 x64 架構的 Windows 上有效。 在適用于 ARM 裝置的 Windows 上，左移和右移位運算子的執行方式明顯不同。 如需詳細資訊，請參閱[HELLO ARM](https://devblogs.microsoft.com/cppblog/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c/) blog 文章的「移位運算子」一節。

## <a name="left-shifts"></a>左移位

左移運算子會使*shift 運算式*中的位向左移動加總*運算式*所指定的位置數目。 移位作業空出的位元位置以零填補。 左移是邏輯移位 (會捨棄移出結尾的位元，包括正負號位元)。 如需位移位類型的詳細資訊，請參閱[位移位](https://en.wikipedia.org/wiki/Bitwise_shift)。

下列範例示範使用不帶正負號數字的左移位作業。 此範例以值代表 bitset 說明位元的行為。 如需詳細資訊，請參閱[Bitset 類別](../standard-library/bitset-class.md)。

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

如果將帶正負號的數字左移，以影響正負號位元，結果會是未定義。 下列範例顯示當1位被左移至符號位位置時，會發生什麼事。

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

右移運算子會使*shift 運算式*中的位模式向右移位（由加總*運算式*所指定的位置數目）。 若是不帶正負號的數字，移位作業空出的位元位置以零填補。 若是帶正負號的數字，會使用正負號位元填補空出的位元位置。 換句話說，如果是正數就會使用 0，負數則使用 1。

> [!IMPORTANT]
> 將帶正負號負數向右移的結果與實作相關。 雖然 Microsoft c + + 編譯器會使用正負號來填補空出的位位置，但並不保證其他的實現也會這麼做。

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

移位運算子兩邊的運算式都必須是整數類型。 整數提升會根據[標準轉換](standard-conversions.md)中所述的規則來執行。 結果的類型與已升級之*移位運算式*的類型相同。

在下列範例中， **char**類型的變數會升級為**int**。

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

如果*加法運算式*為負數，或是加總*運算式*大於或等於（升級）*移位運算式*中的位數，則移位運算的結果會是未定義的。 如果*加法類運算式*為0，則不會執行任何移位作業。

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

<sup>1</sup>以下是 c + + 11 ISO 規格（INCITS/ISO/IEC 14882-2011 [2012]）、區段5.8.2 和5.8.3 中的 shift 運算子描述。

`E1 << E2` 的值是向左移位 `E1` 的 `E2` 位元位置；空出的位元會以零填補。 如果 `E1` 具有不帶正負號的類型，結果的值會是**E1 × 2**<sup>**E2**</sup>，比結果類型中可顯示的最大值還要少一個模數。 否則，如果 `E1` 具有帶正負號的類型和非負數值，且**E1 × 2**<sup>**E2**</sup>可在結果類型的對應不帶正負號類型中顯示，則轉換為結果類型的值會是產生的值; 否則，行為會是未定義的。

`E1 >> E2` 的值是 `E1` 向右移位 `E2` 個位元位置。 如果 `E1` 具有不帶正負號的類型，或如果具有帶正負號的 `E1` 類型和非負數值，則結果的值會是**E1/2**<sup>**E2**</sup>之商的整數部分。 如果 `E1` 的類型帶正負號，且具有負數值，結果產生的值由實作決定。

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
