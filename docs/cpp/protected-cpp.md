---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 79ca081726c1f26a251763e2533ade730f075e2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317272"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>語法

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>備註

**受保護的**關鍵字指定對*成員清單中*的類成員的訪問,以下一個訪問指定器(**公共**或**私有**)或類定義的結尾進行存取。 宣告為**受保護的**類成員只能由以下人員使用:

- 原本宣告這些成員之類別的成員函式。

- 原本宣告這些成員之類別的 Friend。

- 從原本宣告這些成員的類別中所衍生，具有 public 或 protected 存取權限的類別。

- 直接以 private 方式衍生的類別，這些類別也具有對 protected 成員的 private 存取權限。

在基類名稱之前,**受保護**關鍵字指定基類的公共成員和受保護成員是其派生類的保護成員。

受保護成員不像**私有**成員那樣私有,只有聲明成員才能訪問這些成員,但它們不像公共成員那樣公開,而**公共**成員在任何功能中都可以訪問。

派生類的任何友元或成員函數都可以訪問也聲明為**靜態**的受保護成員。 派生類中的好友和成員函數只能通過指向派生類的指標、引用或對象訪問未聲明為**靜態**的受保護成員。

有關相關信息,請參閱[控制對類成員的訪問](member-access-control-cpp.md)中[的朋友](../cpp/friend-cpp.md)、[公共](../cpp/public-cpp.md)、[私有](../cpp/private-cpp.md)和成員存取表。

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中,C++訪問指定器關鍵字(**公共**、**私有**和**受保護**)可能會影響類型和方法對程式集的可見性。 有關詳細資訊,請參閱[成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
> 使用[/LN](../build/reference/ln-create-msil-module.md)編譯的檔不受此行為的影響。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

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
