---
title: 加法類運算子：+ 和 -
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- operators [C++], addition
- subtraction operator [C++], additive operators
- + operator [C++], additive operators
- additive operators [C++]
- arithmetic operators [C++], additive operators
- '- operator [C++], additive operators in C++'
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
ms.openlocfilehash: 2601debb0a21c4ab9cdcedb25b26085a1aff0a1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370201"
---
# <a name="additive-operators--and--"></a>加法類運算子：+ 和 -

## <a name="syntax"></a>語法

```
expression + expression
expression - expression
```

## <a name="remarks"></a>備註

加法類運算子為：

- 加法**+**( )

- 減法**-**( )

這些二進位運算子具有由左至右的順序關聯性。

加法類運算子接受算術或指標類型運算元。 添加**+**( ) 運算子的結果是操作數的總和。 減法**-**() 運算符的結果是操作數之間的差異。 如果一個或兩個運算元為指標，它們必須是物件的指標，而不是函式的指標。 如果兩個運算元都是指標，除非兩個運算元都是同一個陣列中的物件指標，否則結果並沒有意義。

加法運算符採用*算術*、*積分*和*標量*類型的操作數。 其定義如下表所列。

### <a name="types-used-with-additive-operators"></a>搭配加法類運算子使用的類型

|類型|意義|
|----------|-------------|
|*演演算法*|整數和浮點類型統稱為「算術」類型。|
|*積分*|各種大小 (long、short) 的 char 和 int 及列舉是「整數」類型。|
|*純量 (scalar)*|純量運算元是算術或指標類型的運算元。|

這些運算子的有效組合包括：

*算術* + *arithmetic*

*標量* + *積分*

*整體* + *標量*

*算術* - *arithmetic*

*黃* - *牛標量*

請注意，加法和減法並非對等的運算。

如果兩個操作數都是算術類型,則[標準轉換](standard-conversions.md)中介紹的轉換將應用於操作數,並且結果是轉換的類型。

## <a name="example"></a>範例

```cpp
// expre_Additive_Operators.cpp
// compile with: /EHsc
#include <iostream>
#define SIZE 5
using namespace std;
int main() {
   int i = 5, j = 10;
   int n[SIZE] = { 0, 1, 2, 3, 4 };
   cout  << "5 + 10 = " << i + j << endl
         << "5 - 10 = " << i - j << endl;

   // use pointer arithmetic on array

   cout << "n[3] = " << *( n + 3 ) << endl;
}
```

## <a name="pointer-addition"></a>指標加法

如果其中一個加法運算的運算元是物件陣列的指標，其他運算元必須是整數類型。 結果會是與原始指標相同類型且指向另一個陣列元素的指標。 下列程式碼片段說明這個概念：

```cpp
short IntArray[10]; // Objects of type short occupy 2 bytes
short *pIntArray = IntArray;

for( int i = 0; i < 10; ++i )
{
    *pIntArray = i;
    cout << *pIntArray << "\n";
    pIntArray = pIntArray + 1;
}
```

雖然已將整數值 1 加入至 `pIntArray`，但並不代表「對位址加 1」，而是表示「將指標調整為指向陣列中的下一個物件」，而其距離正好是 2 個位元組 (或 `sizeof( int )`)。

> [!NOTE]
> `pIntArray = pIntArray + 1` 形式的程式碼在 C++ 程式中很少見，若要執行遞增作業，使用下列形式會更好：`pIntArray++` 或 `pIntArray += 1`。

## <a name="pointer-subtraction"></a>指標減法

如果兩個運算元都是指標，則減法運算的結果為兩個運算元之間的差數 (以陣列元素為單位)。 減法運算式生成類型`ptrdiff_t`的簽名積分結果(在標準中定義,包括檔\<stddef.h>)。

兩個運算元中的第二個運算元可以是整數類資料類型。 減法運算的結果與原始指標的類型相同。 減法的值是指向 *(n* - *i*) th 陣列元素的指標,其中*n*是原始指標指向的元素 *,i*是第二個操作數的整數值。

## <a name="see-also"></a>另請參閱

[具有二元運算子的運算式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 加法類運算子](../c-language/c-additive-operators.md)
