---
title: static_cast 運算子
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 37708bf50b28eb120af8e8a79e770c3121e6f509
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178583"
---
# <a name="static_cast-operator"></a>static_cast 運算子

根據運算式中出現的類型，將*運算式*轉換為*類型識別碼*的類型。

## <a name="syntax"></a>語法

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>備註

標準 C++ 不會利用執行階段類型檢查來確認轉換是否安全。 在 C++/CX 中會執行編譯時期和執行階段檢查。 如需詳細資訊，請參閱 [轉型](casting.md)中定義的介面的私用 C++ 專屬實作。

**Static_cast**運算子可以用於作業，例如將基類的指標轉換為衍生類別的指標。 這類轉換不一定一直都是安全的。

在一般情況下，當您想要將數值資料類型（例如列舉的列舉）轉換成浮點數或整數時，您會使用**static_cast** ，而且您一定會有轉換所涉及的資料類型。 **static_cast**轉換與**dynamic_cast**轉換並不安全，因為**static_cast**不會執行任何執行時間類型檢查，而是**dynamic_cast** 。 不明確指標的**dynamic_cast**將會失敗，而**static_cast**會傳回，如同沒有任何錯誤;這可能會造成危險。 雖然**dynamic_cast**轉換更為安全，但**dynamic_cast**僅適用于指標或參考，而執行時間類型檢查則是額外負荷。 如需詳細資訊，請參閱[Dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)。

在下列範例中，`D* pd2 = static_cast<D*>(pb);` 這一行並不安全，因為 `D` 可能會包含不在 `B` 中的欄位和方法。 不過，`B* pb2 = static_cast<B*>(pd);` 這一行是安全的轉換，因為 `D` 一律都會包含所有的 `B`。

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

相較于[dynamic_cast](../cpp/dynamic-cast-operator.md)，不會對 `pb`的**static_cast**轉換進行執行時間檢查。 `pb` 所指向的物件可能不是 `D` 類型的物件，在此情況下，使用 `*pd2` 可能會得不償失。 例如，呼叫屬於 `D` 類別但不屬於 `B` 類別的成員函式時，可能會造成存取違規。

**Dynamic_cast**和**static_cast**運算子會將指標移至整個類別階層。 不過， **static_cast**只依賴 cast 語句中提供的資訊，因此可能不安全。 例如：

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

如果 `pb` 真的指向 `D` 類型的物件，則 `pd1` 和 `pd2` 會取得相同的值。 如果 `pb == 0`，它們也會得到相同的值。

如果 `pb` 指向類型的物件 `B` 而不是完整的 `D` 類別，則**dynamic_cast**會知道足以傳回零。 不過， **static_cast**依賴程式設計人員的判斷提示，`pb` 指向類型 `D` 的物件，並且只會傳回應 `D` 物件的指標。

因此， **static_cast**可以執行隱含轉換的反向動作，在此情況下，結果會是未定義的。 它留給程式設計人員確認**static_cast**轉換的結果是安全的。

此行為也適用於類別類型以外的類型。 例如， **static_cast**可以用來從 int 轉換成**char**。 不過，產生的**char**可能沒有足夠的位來容納整個**int**值。 同樣地，它會留給程式設計人員確認**static_cast**轉換的結果是否安全。

**Static_cast**運算子也可以用來執行任何隱含的轉換，包括標準轉換和使用者定義的轉換。 例如：

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

**Static_cast**運算子可以明確地將整數值轉換為列舉類型。 如果整數類型的值不在列舉值的範圍內，所產生的列舉值就是未定義的值。

**Static_cast**運算子會將 null 指標值轉換為目的地類型的 null 指標值。

**Static_cast**運算子可以將任何運算式明確轉換成 void 類型。 目的地 void 型別可以選擇性地包含**const**、 **volatile**或 **__unaligned**屬性。

**Static_cast**運算子無法轉換成**const**、 **volatile**或 **__unaligned**屬性。 如需移除這些屬性的詳細資訊，請參閱[Const_cast 運算子](../cpp/const-cast-operator.md)。

**C++/Cli：** 由於在重新配置的垃圾收集行程之上執行未檢查的轉換，因此使用**static_cast**應該只在效能關鍵的程式碼中，才能正常運作。 如果您必須在 [發行] 模式中使用**static_cast** ，請將它取代為您的偵錯工具組建中的[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)以確保成功。

## <a name="see-also"></a>另請參閱

[轉型運算子](../cpp/casting-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
