---
title: register 儲存類別指定名稱
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 513213222ee2c598455709a0891977a0949c8555
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229554"
---
# <a name="register-storage-class-specifier"></a>register 儲存類別指定名稱

**Microsoft 特定的**

Microsoft C/C++ 編譯器不接受使用者要求的暫存器變數。 不過，如果是可攜性， **`register`** 編譯器會接受與關鍵字相關聯的所有其他語法。 例如，您無法將一元傳址運算子（ **&** ）套用至 register 物件，也不可以在 **`register`** 陣列上使用關鍵字。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[內部層級宣告的儲存類別指定名稱](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
