---
title: '後置遞增和遞減運算子: + + 和-|Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4591f9f4fed8b3b8dd1c24b8200b3365d87194b8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044661"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>後置遞增和遞減運算子：++ 和 --

## <a name="syntax"></a>語法

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>備註

C++ 提供前置和後置遞增及遞減運算子，本節只說明後置遞增和遞減運算子。 (如需詳細資訊，請參閱 <<c0> [ 前置遞增和遞減運算子](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)。)兩者之間的差異是在後置標記法中，會出現在運算子*後置運算式*，而在前置標記法中，運算子會出現之前*運算式。* 下列範例顯示後置遞增運算子：

```cpp
i++;
```

套用後置遞增運算子的效果 (**++**) 是運算元的值會增加一個單位的適當的型別。 同樣地，套用後置遞減運算子的效果 (**--**) 是運算元的值會減少一個單位的適當的型別。

請務必請注意，後置遞增或遞減運算式會評估運算式的值為*之前*個別運算子的應用程式。 遞增或遞減運算，就會發生*之後*則會評估運算元。 此問題只有在較大運算式的內容中進行後置遞增或遞減運算時發生。

使用後置運算子當做函式的引數時，引數的值在傳遞至函式之前不保證會遞增或遞減。  如需詳細資訊，請參閱 C++ 標準中的 1.9.17 一節。

將後置遞增運算子套用至類型的物件陣列的指標**長**實際上是新增四個指標的內部表示法。 這個行為會導致先前參考的指標*n*個元素的陣列，請參閱 (*n*+ 1) 個項目。

後置遞增和後置遞減運算子的運算元必須是可修改 (不**const**) 左值的算術或指標類型。 結果的型別是相同*後置運算式*，但已不再是左值。

**Visual Studio 2017 版本 15.3 和更新版本**(適用於[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): 運算元的後置遞增或遞減運算子可能不是類型**bool**。

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