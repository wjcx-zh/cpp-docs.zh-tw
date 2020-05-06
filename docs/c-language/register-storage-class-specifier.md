---
title: register 儲存類別指定名稱
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 0fac6db2254a909d0ec558a7e76f7ccf32aa7ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325243"
---
# <a name="register-storage-class-specifier"></a>register 儲存類別指定名稱

**Microsoft 特定的**

Microsoft C/C++ 編譯器不接受使用者要求的暫存器變數。 不過，為了提供可攜性，編譯器接受其他所有與 **register** 關鍵字相關的語意。 例如，您無法將一元傳址運算子（**&**）套用至 register 物件，也不能在陣列上使用**register**關鍵字。

**結束 Microsoft 專有**

## <a name="see-also"></a>請參閱

[內部層級宣告的儲存類別指定名稱](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
