---
title: 不適當的等位存取
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 5a804ed80c8f1ac2f5dd9a24f12c67e96e199b6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227825"
---
# <a name="improper-access-to-a-union"></a>不適當的等位存取

**ANSI 3.3.2.3**：使用不同類型的成員存取等位物件的成員

如果宣告了兩種類型的等位並且儲存一個值，但等位是以另一種類型存取，則結果不可靠。

例如，會宣告和的聯集 **`float`** **`int`** 。 **`float`** 會儲存值，但程式稍後會以的形式存取值 **`int`** 。 在這種情況下，值會取決於值的內部儲存 **`float`** 。 整數值會變得不可靠。

## <a name="see-also"></a>另請參閱

[結構、等位、列舉和位欄位](../c-language/structures-unions-enumerations-and-bit-fields.md)
