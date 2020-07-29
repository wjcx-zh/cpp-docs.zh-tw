---
title: 儲存類別指定名稱與函式宣告
ms.date: 11/04/2016
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
ms.openlocfilehash: e27cc6ac748c0af3063dbc5b608114761da8b7dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211693"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>儲存類別指定名稱與函式宣告

您可以 **`static`** **`extern`** 在函式宣告中使用或儲存類別規範。 函式一定會具有全域存留期。

**Microsoft 特定的**

內部層次的函式宣告與外部層次的函式宣告具有相同的意義。 這表示函式從其宣告的位置到轉譯單位的其餘部分皆可見，即使是在區域範圍宣告亦相同。

**結束 Microsoft 專有**

函式的可視性規則與變數的規則稍有不同，如下所示：

- 宣告為的函式 **`static`** 只有在其定義所在的原始檔中才可見。 相同原始程式檔中的函式可以呼叫函式 **`static`** ，但其他原始程式檔中的函式無法直接依名稱存取該函式。 您可以在不同的來源檔案中宣告另一個 **`static`** 具有相同名稱的函式，而不會發生衝突。

- 宣告為的函式在 **`extern`** 程式的所有原始程式檔中都是可見的（除非您稍後將這類函式重新宣告為 **`static`** ）。 任何函式都可以呼叫 **`extern`** 函數。

- 預設會省略儲存類別規範的函式宣告 **`extern`** 。

**Microsoft 特定的**

Microsoft 允許將識別碼重新定義 **`extern`** 為 **`static`** 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[C 儲存類別](../c-language/c-storage-classes.md)
