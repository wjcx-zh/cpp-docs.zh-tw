---
title: 繼承 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 214900f8f36de0fa90ffcd6ca75f3a4e6e2c0777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178248"
---
# <a name="inheritance--c"></a>繼承 (C++)

本節將說明如何使用衍生類別產生可擴充程式。

## <a name="overview"></a>概觀

使用稱為「繼承」的機制，可以從現有類別衍生新的類別（請參閱從[單一繼承](../cpp/single-inheritance.md)開始的資訊）。 供衍生使用的類別稱為特定衍生類別的「基底類別」。 衍生類別會使用下列語法宣告：

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

在類別的標記 (名稱) 後方會有一個冒號後面接著基底規格的清單。  基底類別必須先宣告，因此如此命名。  基底規格可能包含存取規範，這是**公用**、**受保護**或**私**用的其中一個關鍵字。  這些存取指定名稱會出現在基底類別名稱的前方，並且只會套用至該基底類別。  這些指定名稱可控制衍生類別使用基底類別成員的權限。  如需存取基類成員的資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。  如果省略存取規範，則會將該基底的存取權視為**私**用。  基底規格可能包含關鍵字**virtual** ，以表示虛擬繼承。  這個關鍵字會顯示在存取指定名稱的前方或後方 (如果有的話)。  如果使用虛擬繼承，則會將基底類別稱為是虛擬基底類別。

您可以指定多個基底類別 (以逗號分隔)。  如果指定了單一基類，繼承模型就是[單一繼承](../cpp/single-inheritance.md)。如果指定了一個以上的基類，則繼承模型稱為[多重繼承](../cpp/multiple-base-classes.md)。

本文包含下列主題：

- [單一繼承](../cpp/single-inheritance.md)

- [多個基類](../cpp/multiple-base-classes.md)

- [虛擬函式](../cpp/virtual-functions.md)

- [明確覆寫](../cpp/explicit-overrides-cpp.md)

- [抽象類別](../cpp/abstract-classes-cpp.md)

- [範圍規則的摘要](../cpp/summary-of-scope-rules.md)

[__Super](../cpp/super.md)和[__interface](../cpp/interface.md)關鍵字記載于本節。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)
