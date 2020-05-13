---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: bf8293c6a6cf12154b02979de08035807991052c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376044"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>語法

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>備註

在類成員清單之前 **,public**關鍵字指定可從任何函數訪問這些成員。 這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。

在基類名稱之前 **,public**關鍵字指定基類的公共成員和保護成員分別是派生類的公共成員和受保護成員。

類別中成員的預設存取方式是 private。 結構或等位中成員的預設存取方式是 public。

對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。 等位不可以具有基底類別。

有關詳細資訊,請參閱[私有](../cpp/private-cpp.md)、[受保護](../cpp/protected-cpp.md)、[好友](../cpp/friend-cpp.md)與成員存取表,[以控制對類別成員的存取](member-access-control-cpp.md)。

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中,C++訪問指定器關鍵字(**公共**、**私有**和**受保護**)可能會影響類型和方法對程式集的可見性。 有關詳細資訊,請參閱[成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
> 使用[/LN](../build/reference/ln-create-msil-module.md)編譯的檔不受此行為的影響。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

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
