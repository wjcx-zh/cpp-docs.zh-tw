---
title: 儲存類別
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
ms.openlocfilehash: 872a014dfc7c21b46f9af810f1cb3463016c7e09
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211680"
---
# <a name="storage-class"></a>儲存類別

函式定義中的儲存類別規範會提供函數 **`extern`** 或 **`static`** 儲存類別。

## <a name="syntax"></a>語法

*函式定義*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

/\**屬性-seq*是 Microsoft 特有的\*/

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*儲存類別規範*：/ \* 用於函式定義\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`extern`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`static`**

如果函式定義不包含*儲存類別規範*，則儲存類別會預設為 **`extern`** 。 您可以明確地將函式宣告為 **`extern`** ，但不是必要的。

如果函式的宣告包含*儲存類別規範* **`extern`** ，則識別碼的連結會與具有檔案範圍之識別碼的任何可見宣告相同。 如果沒有具有檔案範圍的可見宣告，表示識別項具有外部連結。 如果識別項具有檔案範圍，但沒有 *storage-class-specifier*，表示識別項具有外部連結。 外部連結是指，識別項的每個執行個體表示相同的物件或函式。 如需連結和檔案範圍的詳細資訊，請參閱[存留期、範圍、可視性和連結](../c-language/lifetime-scope-visibility-and-linkage.md)。

除了產生錯誤以外，區塊範圍函數宣告的儲存類別規範除外 **`extern`** 。

具有儲存類別的函式 **`static`** 只有在其定義所在的來源檔案中才可見。 所有其他函式（不論是 **`extern`** 明確或隱含地指定儲存類別）都會顯示在程式的所有原始程式檔中。 如果 **`static`** 需要儲存類別，則必須在函式的第一次出現宣告（如果有的話），以及函式的定義上宣告。

**Microsoft 特定的**

啟用 Microsoft 擴充功能時， **`extern`** **`static`** 如果函式定義位於相同的原始檔中，而且定義明確指定了儲存類別，則會為原本宣告但不含儲存類別（或具有儲存類別）的函式指定儲存類別 **`static`** 。

使用/Ze 編譯器選項進行編譯時，使用關鍵字在區塊內宣告的函式 **`extern`** 具有全域可見度。 但使用 /Za 編譯時就不是這種情況。 如果將原始程式碼的可攜性納入考量，則不應倚賴這項功能。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[C 函式定義](../c-language/c-function-definitions.md)
