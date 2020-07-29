---
title: 後置遞增和遞減運算子：++ 和 --
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: 8c3eeb47ec81f4073452c17f40eb2fec4911989f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213277"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>後置遞增和遞減運算子：++ 和 --

## <a name="syntax"></a>語法

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>備註

C++ 提供前置和後置遞增及遞減運算子，本節只說明後置遞增和遞減運算子。 （如需詳細資訊，請參閱[前置遞增和遞減運算子](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)）。兩者的差異在於，在後置標記法中，運算子會出現在後置*運算式*之後，而在前置標記法中，運算子會出現在*expression 之前。* 下列範例顯示後置遞增運算子：

```cpp
i++;
```

套用後置遞增運算子（）的效果 **++** 是運算元的值會增加一個單位的適當類型。 同樣地，套用後置遞減運算子（）的效果， **--** 是運算元的值會減少一個單位的適當類型。

請務必注意，後置遞增或遞減運算式會評估為運算式的值，然後*再進行*個別運算子的應用。 遞增或遞減運算會在運算元評估*之後*發生。 此問題只有在較大運算式的內容中進行後置遞增或遞減運算時發生。

使用後置運算子當做函式的引數時，引數的值在傳遞至函式之前不保證會遞增或遞減。  如需詳細資訊，請參閱 C++ 標準中的 1.9.17 一節。

將後置遞增運算子套用至類型物件陣列的指標時，實際上會在 **`long`** 指標的內部標記法中加入四個。 這個行為會導致指標（先前參考陣列的第*n*個元素）參考（*n*+ 1）個元素。

後置遞增和後置遞減運算子的運算元，必須可修改（不是 **`const`** ）算術或指標類型的左值。 結果的型別與後置*運算式*的類型相同，但不再是左值。

**Visual Studio 2017 15.3 和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：後置遞增或遞減運算子的運算元不可以是類型 **`bool`** 。

下列程式碼示範後置遞增運算子：

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

不支援在列舉類型上進行後置遞增和後置遞減運算：

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>另請參閱

[後置運算式](../cpp/postfix-expressions.md)<br/>
[C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 後置遞增和遞減運算子](../c-language/c-postfix-increment-and-decrement-operators.md)
