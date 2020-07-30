---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 0f6b58896cbcb11901721125f9b1a32a99acb357
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227136"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>語法

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>備註

在類別成員清單前面時， **`public`** 關鍵字會指定可以從任何函式存取這些成員。 這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。

在基類的名稱前面， **`public`** 關鍵字會指定基類的 public 和 protected 成員分別為衍生類別的 public 和 protected 成員。

類別中成員的預設存取方式是 private。 結構或等位中成員的預設存取方式是 public。

對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。 等位不可以具有基底類別。

如需詳細資訊，請參閱[私](../cpp/private-cpp.md)用、[受保護](../cpp/protected-cpp.md)、 [Friend](../cpp/friend-cpp.md)和[控制對類別成員的存取](member-access-control-cpp.md)中的成員存取表格。

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中，c + + 存取規範關鍵字（ **`public`** 、 **`private`** 和 **`protected`** ）可能會影響元件的類型和方法可見度。 如需詳細資訊，請參閱[成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
> 以[/LN](../build/reference/ln-create-msil-module.md)編譯的檔案不會受到此行為的影響。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

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
