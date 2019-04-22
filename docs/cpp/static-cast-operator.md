---
title: static_cast 運算子
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: dca6d5297379e6ddc1c70dba80f35f2f55672e49
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776917"
---
# <a name="staticcast-operator"></a>static_cast 運算子

將轉換*運算式*的型別*型別 id，* 只根據出現在運算式中的類型。

## <a name="syntax"></a>語法

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>備註

標準 C++ 不會利用執行階段類型檢查來確認轉換是否安全。 在 C++/CX 中會執行編譯時期和執行階段檢查。 如需詳細資訊，請參閱 [轉型](casting.md)中定義的介面的私用 C++ 專屬實作。

**Static_cast**運算子可以用於作業，例如將指標轉換成基底類別，衍生類別的指標。 這類轉換不一定一直都是安全的。

您所使用的一般**static_cast**當您想要將列舉之類的數值資料類型轉換為 int 或 int 至浮點數，而且您特定的資料型別中涉及轉換。 **static_cast**轉換不是安全性不如**dynamic_cast**轉換，因為**static_cast**沒有任何執行階段類型檢查，但**dynamic_cast**會執行。 A **dynamic_cast**模稜兩可的指標將會失敗，雖然**static_cast**會傳回而看似沒有任何錯誤; 這可能會造成危險。 雖然**dynamic_cast**轉換為更安全**dynamic_cast**只適用於指標或參考和執行階段類型檢查會有額外負荷。 如需詳細資訊，請參閱 < [dynamic_cast 運算子](../cpp/dynamic-cast-operator.md)。

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

相對於[dynamic_cast](../cpp/dynamic-cast-operator.md)，沒有執行階段檢查對**static_cast**轉換`pb`。 `pb` 所指向的物件可能不是 `D` 類型的物件，在此情況下，使用 `*pd2` 可能會得不償失。 例如，呼叫屬於 `D` 類別但不屬於 `B` 類別的成員函式時，可能會造成存取違規。

**Dynamic_cast**並**static_cast**運算子移動整個類別階層架構的指標。 不過， **static_cast**完全依賴 cast 陳述式中提供的資訊，因此可能不安全。 例如: 

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

如果`pb`指向的物件型別的`B`而非完整`D`類別，則**dynamic_cast**會知道要傳回零。 不過， **static_cast**依賴程式設計人員的判斷提示，`pb`指向的物件型別的`D`只會傳回該假設性的指標和`D`物件。

因此， **static_cast**可以進行反向隱含轉換，在此情況下，結果便未定義。 它就程式設計人員必須確認的結果**static_cast**轉換是安全的。

此行為也適用於類別類型以外的類型。 比方說， **static_cast**可用來將 int 轉換**char**。 不過，產生**char**可能沒有足夠的位元，以表示整個**int**值。 同樣地，它就程式設計人員必須確認的結果**static_cast**轉換是安全的。

**Static_cast**運算子也可用來執行任何隱含的轉換，包括標準轉換和使用者定義的轉換。 例如: 

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

**Static_cast**運算子可以明確地將整數值轉換成列舉型別。 如果整數類型的值不在列舉值的範圍內，所產生的列舉值就是未定義的值。

**Static_cast**運算子會將 null 指標值轉換成目的地類型的 null 指標值。

任何運算式明確轉換為 void 類型**static_cast**運算子。 目的 void 類型可以選擇性地包含**const**， **volatile**，或 **__unaligned**屬性。

**Static_cast**運算子不能**const**， **volatile**，或 **__unaligned**屬性。 請參閱[const_cast 運算子](../cpp/const-cast-operator.md)如需移除這些屬性的詳細資訊。

**C++/ CLI:** 因為執行未檢查的轉換，在重新配置的記憶體回收行程，使用的最上層的危險**static_cast**只在效能關鍵程式碼時應該確定它能正常運作。 如果您必須使用**static_cast**在發行模式中，使用替代與[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)在您的偵錯組建，以確保成功。

## <a name="see-also"></a>另請參閱

[轉型運算子](../cpp/casting-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)