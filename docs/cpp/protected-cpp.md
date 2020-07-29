---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 25b25447737a075bcf4f02f1c3049c996fb4c678
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227162"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>語法

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>備註

**`protected`** 關鍵字會指定*成員清單*中類別成員的存取權，直到下一個存取規範（ **`public`** 或 **`private`** ）或類別定義的結尾。 宣告為的類別成員只能 **`protected`** 由下列各項使用：

- 原本宣告這些成員之類別的成員函式。

- 原本宣告這些成員之類別的 Friend。

- 從原本宣告這些成員的類別中所衍生，具有 public 或 protected 存取權限的類別。

- 直接以 private 方式衍生的類別，這些類別也具有對 protected 成員的 private 存取權限。

在基類的名稱前面時， **`protected`** 關鍵字會指定基類的 public 和 protected 成員是其衍生類別的受保護成員。

受保護的成員不是私用成員，只有在其宣告的 **`private`** 類別成員才可存取，但它們不是 public **`public`** 成員，而是可在任何函式中存取。

也宣告為的受保護成員可供 **`static`** 衍生類別的任何 friend 或成員函式存取。 未宣告為的受保護成員 **`static`** ，只能透過衍生類別的指標、參考或物件，在衍生類別中存取 friend 和成員函式。

如需相關資訊，請參閱[friend](../cpp/friend-cpp.md)、 [public](../cpp/public-cpp.md)、 [Private](../cpp/private-cpp.md)和[控制對類別成員的存取](member-access-control-cpp.md)中的成員存取表格。

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中，c + + 存取規範關鍵字（ **`public`** 、 **`private`** 和 **`protected`** ）可能會影響元件的類型和方法可見度。 如需詳細資訊，請參閱[成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
> 以[/LN](../build/reference/ln-create-msil-module.md)編譯的檔案不會受到此行為的影響。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

## <a name="end-clr-specific"></a>/clr 專屬資訊結束

## <a name="example"></a>範例

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>另請參閱

[控制對類別成員的存取](member-access-control-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
