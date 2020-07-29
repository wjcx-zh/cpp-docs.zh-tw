---
title: 左值和右值運算式
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: 0c287c45f2d7ea121c9c706b3b761ff7ce6ec232
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199824"
---
# <a name="l-value-and-r-value-expressions"></a>左值和右值運算式

參考記憶體位置的運算式稱為「左值」運算式。 左值代表儲存區域的「定位器」值或「左」值，表示它可以出現在等號（）的左邊 **=** 。 左值通常是識別項。

參考可修改位置的運算式稱為「可修改的左值」。 可修改的左值不可具有陣列類型、不完整的類型，或具有屬性的類型 **`const`** 。 若要讓結構和等位成為可修改的左值，它們不能有任何具有屬性的成員 **`const`** 。 識別項的名稱表示儲存位置，而變數值是指儲存在該位置的值。

如果識別項參考記憶體位置且其類行為算術、結構、等位或指標，該識別項就是可修改的左值。 例如，如果 `ptr` 是儲存區域的指標，則 `*ptr` 是指定 `ptr` 所指向之儲存區域的可修改左值。

下列任何 C 運算式都可以是左值運算式：

- 整數類資料、浮點、指標、結構或等位型別的識別項。

- 不會評估為陣列的下標 (**[ ]**) 運算式

- 成員選取運算式（ **->** 或） **。**

- 未參考陣列的一元間接取值（ <strong>\*</strong> ）運算式

- 括號內的左值運算式

- **`const`** 物件（不可修改的左值）

「右值」這個詞有時用來描述運算式的值，並且與左值做區分。 所有左值都是右值，但並非所有右值都是左值。

**Microsoft 特定的**

Microsoft C 包含 ANSI C 標準擴充功能，只要物件的大小未透過轉型延伸，就可將左值轉型做為左值使用  （如需詳細資訊，請參閱[類型](../c-language/type-cast-conversions.md)轉換）。下列範例說明這項功能：

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

Microsoft C 預設會啟用 Microsoft 擴充功能。 使用 /Za 編譯器選項可停用這些擴充功能。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[運算元和運算式](../c-language/operands-and-expressions.md)
