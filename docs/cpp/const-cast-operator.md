---
title: const_cast 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 314e8363fafa4f2a6649055f2c608cd5b7edd18c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070072"
---
# <a name="constcast-operator"></a>const_cast 運算子

移除**const**， **volatile**，並 **__unaligned**自類別的屬性。

## <a name="syntax"></a>語法

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>備註

任何物件類型的指標或資料成員的指標可以明確地轉換成類型相同，除了**const**， **volatile**，並 **__unaligned**限定詞。 對於指標和參考，其結果會參考原始物件。 對於資料成員的指標，則結果會參考與資料成員的原始 (未轉型) 指標相同的成員。 根據所參考物件的類型，透過產生的指標、參考或資料成員的指標進行寫入作業，可能會產生未定義的行為。

您無法使用**const_cast**運算子直接覆寫常數變數的常數狀態。

**Const_cast**運算子會將 null 指標值轉換成目的地類型的 null 指標值。

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

在上一行包含**const_cast**的資料類型**這**指標`const CCTest *`。 **Const_cast**運算子會變更的資料型別**這**指標`CCTest *`，讓成員`number`修改。 轉換只會在其出現之陳述式的其餘部分中持續進行。

## <a name="see-also"></a>另請參閱

[轉型運算子](../cpp/casting-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)