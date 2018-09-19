---
title: 繼承 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e49e115f6ef4269ddfc7169add6a88e3bb0c54f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46064551"
---
# <a name="inheritance--c"></a>繼承 (C++)

本節將說明如何使用衍生類別產生可擴充程式。

## <a name="overview"></a>總覽

新的類別可以衍生自現有的類別使用的機制稱為 「 繼承 」 (請參閱在一開始的資訊[單一繼承](../cpp/single-inheritance.md))。 供衍生使用的類別稱為特定衍生類別的「基底類別」。 衍生類別會使用下列語法宣告：

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

在類別的標記 (名稱) 後方會有一個冒號後面接著基底規格的清單。  基底類別必須先宣告，因此如此命名。  基底規格可能包含存取規範，也就是其中一個關鍵字**公開金鑰**，**保護**或是**私人**。  這些存取指定名稱會出現在基底類別名稱的前方，並且只會套用至該基底類別。  這些指定名稱可控制衍生類別使用基底類別成員的權限。  請參閱[成員存取控制](../cpp/member-access-control-cpp.md)如需存取基底類別成員的資訊。  如果省略存取規範，則該基底的存取會被視為**私人**。  基底規格可能包含關鍵字**虛擬**表示虛擬繼承。  這個關鍵字會顯示在存取指定名稱的前方或後方 (如果有的話)。  如果使用虛擬繼承，則會將基底類別稱為是虛擬基底類別。

您可以指定多個基底類別 (以逗號分隔)。  指定單一基底類別，則繼承模型是否[單一繼承](../cpp/single-inheritance.md)。如果指定一個以上的基底類別，則繼承模型稱為[多重繼承](../cpp/multiple-base-classes.md)。

其中包含下列主題：

- [單一繼承](../cpp/single-inheritance.md)

- [多重基底類別](../cpp/multiple-base-classes.md)

- [虛擬函式](../cpp/virtual-functions.md)

- [明確覆寫](../cpp/explicit-overrides-cpp.md)

- [抽象類別](../cpp/abstract-classes-cpp.md)

- [範圍規則摘要](../cpp/summary-of-scope-rules.md)

[__Super](../cpp/super.md)並[__interface](../cpp/interface.md)關鍵字都記錄在這一節。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)