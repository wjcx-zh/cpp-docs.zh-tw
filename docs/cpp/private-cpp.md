---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 002a8ad2887bd711bc3654d8e8910e2bede889d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177556"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>語法

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>備註

在類別成員清單前面時， **private**關鍵字會指定只能從成員函式和類別的 friend 存取這些成員。 這種做法適用於在下一個存取指定名稱或類別結尾之前宣告的所有成員。

在基類的名稱前面時， **private**關鍵字會指定基類的 public 和 protected 成員為衍生類別的私用成員。

類別中成員的預設存取方式是 private。 結構或等位中成員的預設存取方式是 public。

對於類別而言，基底類別的預設存取方式為 private，對於結構而言則為 public。 等位不可以具有基底類別。

如需相關資訊，請參閱[friend](../cpp/friend-cpp.md)、 [public](../cpp/public-cpp.md)、 [Protected](../cpp/protected-cpp.md)和[控制對類別成員的存取](member-access-control-cpp.md)中的成員存取表格。

## <a name="clr-specific"></a>/clr 專屬資訊

在 CLR 類型中， C++存取規範關鍵字（**公用**、**私**用和**受保護**）可能會影響元件的類型和方法可見度。 如需詳細資訊，請參閱[成員存取控制](member-access-control-cpp.md)。

> [!NOTE]
>  以[/LN](../build/reference/ln-create-msil-module.md)編譯的檔案不會受到此行為的影響。 在這種情況下，所有 Managed 類別 (public 或 private) 都會是可見。

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
