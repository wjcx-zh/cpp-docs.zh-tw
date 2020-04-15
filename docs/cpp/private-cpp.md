---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: d6dc1ca309c096a4f5e857ade3d7550749991f3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366211"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>語法

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>備註

在類別成員清單之前,**私有**關鍵字指定這些成員只能從類的成員函數和朋友訪問。 這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。

在基類名稱之前,**私有**關鍵字指定基類的公共和受保護成員是派生類的私有成員。

類別中成員的預設存取方式是 private。 結構或等位中成員的預設存取方式是 public。

對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。 等位不可以具有基底類別。

有關相關信息,請參閱[控制對類成員的訪問](member-access-control-cpp.md)中[的朋友](../cpp/friend-cpp.md)、[公共](../cpp/public-cpp.md)、[受保護](../cpp/protected-cpp.md)和成員存取表。

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中,C++訪問指定器關鍵字(**公共**、**私有**和**受保護**)可能會影響類型和方法對程式集的可見性。 有關詳細資訊,請參閱[成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
> 使用[/LN](../build/reference/ln-create-msil-module.md)編譯的檔不受此行為的影響。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

## <a name="end-clr-specific"></a>/clr 專屬資訊結束

## <a name="example"></a>範例

```cpp
// keyword_private.cpp
class BaseClass {
public:
   // privMem accessible from member function
   int pubFunc() { return privMem; }
private:
   void privMem;
};

class DerivedClass : public BaseClass {
public:
   void usePrivate( int i )
      { privMem = i; }   // C2248: privMem not accessible
                         // from derived class
};

class DerivedClass2 : private BaseClass {
public:
   // pubFunc() accessible from derived class
   int usePublic() { return pubFunc(); }
};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   DerivedClass2 aDerived2;
   aBase.privMem = 1;     // C2248: privMem not accessible
   aDerived.privMem = 1;  // C2248: privMem not accessible
                          //    in derived class
   aDerived2.pubFunc();   // C2247: pubFunc() is private in
                          //    derived class
}
```

## <a name="see-also"></a>另請參閱

[控制對類別成員的存取](member-access-control-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
