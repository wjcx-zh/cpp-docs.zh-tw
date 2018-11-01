---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 1cbe88a80b83caa78972d1e2799c1e0d87d1cb0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470979"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>語法

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>備註

**保護**關鍵字會指定存取中的類別成員*成員清單*到下一個存取規範 (**公用**或**私用**) 或類別定義結尾。 類別成員宣告為**保護**可用只能由下列：

- 原本宣告這些成員之類別的成員函式。

- 原本宣告這些成員之類別的 Friend。

- 從原本宣告這些成員的類別中所衍生，具有 public 或 protected 存取權限的類別。

- 直接以 private 方式衍生的類別，這些類別也具有對 protected 成員的 private 存取權限。

當基底類別，在名稱前面**保護**關鍵字會指定基底類別的 public 和 protected 成員是其衍生類別的 protected 的成員。

受保護的成員並不是做為私用**私人**成員，也就是只在其中宣告它們，但它們不是做為公用類別的成員可以存取**公用**中可存取的成員任何函式。

受保護的成員，也會宣告為**靜態**存取衍生任何的類別 friend 或成員函式。 Protected 成員未宣告為可**靜態**存取朋友和衍生類別只能透過指標、 參考或衍生類別中的物件中的成員函式。

如需相關資訊，請參閱[friend](../cpp/friend-cpp.md)，[公用](../cpp/public-cpp.md)，[私人](../cpp/private-cpp.md)，和中的成員存取表[控制對類別成員存取](member-access-control-cpp.md).

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中，c + + 存取指定名稱關鍵字 (**公用**，**私人**，和**保護**) 可能會影響型別和方法在組件方面的可見性。 如需詳細資訊，請參閱 <<c0> [ 成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
>  使用檔案編譯[/LN](../build/reference/ln-create-msil-module.md)不會受到這個行為。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

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