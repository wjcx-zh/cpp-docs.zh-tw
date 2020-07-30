---
title: const_cast 運算子
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: 36de296d1e871ca759108497922973ddea8e3382
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227552"
---
# <a name="const_cast-operator"></a>const_cast 運算子

**`const`** **`volatile`** **`__unaligned`** 從類別中移除、和屬性。

## <a name="syntax"></a>語法

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>備註

任何物件類型的指標或資料成員的指標可以明確地轉換成與 **`const`** 、和限定詞相同的類型 **`volatile`** **`__unaligned`** 。 對於指標和參考，其結果會參考原始物件。 對於資料成員的指標，則結果會參考與資料成員的原始 (未轉型) 指標相同的成員。 根據所參考物件的類型，透過產生的指標、參考或資料成員的指標進行寫入作業，可能會產生未定義的行為。

您不能使用 **`const_cast`** 運算子直接覆寫常數變數的常數狀態。

**`const_cast`** 運算子會將 null 指標值轉換為目的地類型的 null 指標值。

## <a name="example"></a>範例

```cpp
// expre_const_cast_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CCTest {
public:
   void setNumber( int );
   void printNumber() const;
private:
   int number;
};

void CCTest::setNumber( int num ) { number = num; }

void CCTest::printNumber() const {
   cout << "\nBefore: " << number;
   const_cast< CCTest * >( this )->number--;
   cout << "\nAfter: " << number;
}

int main() {
   CCTest X;
   X.setNumber( 8 );
   X.printNumber();
}
```

在包含的行上 **`const_cast`** ，指標的資料類型 **`this`** 是 `const CCTest *` 。 **`const_cast`** 運算子會將指標的資料類型變更 **`this`** 為 `CCTest *` ，以允許修改該成員 `number` 。 轉換只會在其出現之陳述式的其餘部分中持續進行。

## <a name="see-also"></a>另請參閱

[轉型運算子](../cpp/casting-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
