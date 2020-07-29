---
title: 類別和結構 (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: d593f6575fec64aa0eb14c7aa0fcbb5c4eb66691
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220596"
---
# <a name="classes-and-structs-c"></a>類別和結構 (C++)

本節介紹 C++ 類別和結構。 這兩個建構在 C++ 中相同，差異在於結構中的預設存取範圍是公用，而類別中的預設值是私用。

類別和結構是可讓您定義專屬類型的建構。 類別和結構可以同時包含資料成員和成員函式，以讓您描述類型的狀態和行為。

本文包含下列主題：

- [class](../cpp/class-cpp.md)

- [結構](../cpp/struct-cpp.md)

- [類別成員總覽](../cpp/class-member-overview.md)

- [成員存取控制](../cpp/member-access-control-cpp.md)

- [繼承](../cpp/inheritance-cpp.md)

- [靜態成員](../cpp/static-members-cpp.md)

- [使用者定義型別轉換](../cpp/user-defined-type-conversions-cpp.md)

- [可變動的資料成員 (mutable 規範)](../cpp/mutable-data-members-cpp.md)

- [嵌套類別宣告](../cpp/nested-class-declarations.md)

- [匿名類別類型](../cpp/anonymous-class-types.md)

- [成員的指標](../cpp/pointers-to-members.md)

- [this 指標](../cpp/this-pointer.md)

- [C + + 位欄位](../cpp/cpp-bit-fields.md)

三個類別類型是結構、類別和等位。 它們是使用[struct](../cpp/struct-cpp.md)、 [class](../cpp/class-cpp.md)和[union](../cpp/unions.md)關鍵字來宣告。 下表顯示這三個類別類型的差異。

如需聯集的詳細資訊，[請參閱等](../cpp/unions.md)位。 如需 c + +/CLI 和 c + +/CX 中類別和結構的詳細資訊，請參閱[類別和結構](../extensions/classes-and-structs-cpp-component-extensions.md)。

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>結構、類別和等位的存取控制和條件約束

|結構|類別|等位|
|----------------|-------------|------------|
|類別機碼為**`struct`**|類別機碼為**`class`**|類別機碼為**`union`**|
|預設存取權是 public|預設存取權是 private|預設存取權是 public|
|沒有使用條件約束|沒有使用條件約束|一次只使用一個成員|

## <a name="see-also"></a>另請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)
