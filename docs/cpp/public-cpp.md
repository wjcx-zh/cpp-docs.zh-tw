---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 24cc4dd3cd7e0c893664339e7ad83383839b0b11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600361"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>語法

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>備註

加一份類別成員清單前面時**公開**關鍵字會指定這些成員可以存取從任何函式。 這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。

當基底類別，在名稱前面**公用**關鍵字會指定基底類別的 public 和 protected 成員是公用和受保護的成員，分別為衍生類別。

類別中成員的預設存取方式是 private。 結構或等位中成員的預設存取方式是 public。

對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。 等位不可以具有基底類別。

如需詳細資訊，請參閱 <<c0> [ 私人](../cpp/private-cpp.md)，[保護](../cpp/protected-cpp.md)， [friend](../cpp/friend-cpp.md)，和中的成員存取表[控制對類別成員存取](member-access-control-cpp.md).

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中，c + + 存取指定名稱關鍵字 (**公用**，**私人**，和**保護**) 可能會影響型別和方法在組件方面的可見性。 如需詳細資訊，請參閱 <<c0> [ 成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
>  使用檔案編譯[/LN](../build/reference/ln-create-msil-module.md)不會受到這個行為。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

## <a name="end-clr-specific"></a>/clr 專屬資訊結束

## <a name="example"></a>範例

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>另請參閱

[控制對類別成員的存取](member-access-control-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)