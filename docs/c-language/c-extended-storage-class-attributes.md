---
title: C 擴充的儲存類別屬性
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: 5e1fe80f3bc1f581c6ea05c54409b1e76eacfce7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190217"
---
# <a name="c-extended-storage-class-attributes"></a>C 擴充的儲存類別屬性

**Microsoft 特定的**

有關本主題的最新資訊可以在 [__declspec (C++ 參考)](../cpp/declspec.md) 中找到。

擴充屬性語法可簡化並標準化 Microsoft 專有的 C 語言擴充功能。 使用擴充屬性語法的儲存類別屬性包括 thread、naked、dllimport 及 dllexport。

用於指定儲存類別資訊的擴充屬性語法會使用 __declspec 關鍵字，這個關鍵字會指定特定類型的執行個體要以 Microsoft 專有儲存類別屬性儲存 (thread、naked、dllimport 或 dllexport)。 其他儲存類別修飾詞的範例包括 static 和 extern 關鍵字。 不過，這些關鍵字是 ANSI C 標準的一部分，因此未涵蓋在擴充屬性語法內。

## <a name="syntax"></a>語法

*storage-class-specifier*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec （** *擴充-extended-decl-modifier-seq-修飾詞-seq* **）**  / \*Microsoft 特定\*/

*extended-extended-decl-modifier-seq-修飾詞-seq*： &nbsp; &nbsp; &nbsp; &nbsp; / \* Microsoft 專有\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*擴充-extended-decl-modifier-seq-修飾*詞： &nbsp; &nbsp; &nbsp; &nbsp; / \* Microsoft 專有\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**

空白字元用於分隔宣告修飾詞。 請注意，*extended-decl-modifier-seq* 可以是空的，在這種情況下，__declspec 沒有作用。

thread、naked、dllimport 和 dllexport 儲存類別屬性 (Attribute) 是只屬於其套用所在資料或函式宣告的屬性 (Property)，這些屬性 (Attribute) 並不會重新定義函式本身的類別屬性 (Attribute)。 thread 屬性只會影響資料。 naked 屬性只會影響函式。 dllimport 和 dllexport 屬性會同時影響函式和資料。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[宣告和類型](../c-language/declarations-and-types.md)
