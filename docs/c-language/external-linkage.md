---
title: 外部連結
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 05fd4bd07aca995a938c7744dfd506d2a71b8774
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217086"
---
# <a name="external-linkage"></a>外部連結

如果識別碼在檔案範圍層級的第一個宣告未使用 **`static`** 儲存類別規範，則物件會具有外部連結。

如果函式的識別碼宣告沒有*儲存類別規範*，其連結的判斷會與以*儲存類別規範*宣告的方式完全相同 **`extern`** 。 如果物件的識別項宣告具有檔案範圍，但沒有 *storage-class-specifier*，表示其連結為外部連結。

具有外部連結的識別項名稱所指定的函式或資料物件，會與任何其他具有外部連結的相同名稱宣告所指定的函式或資料物件相同。 這兩種宣告可以位於相同轉譯單位或不同轉譯單位中。 如果物件或函式同時具有全域存留期，則物件或函式會由整個程式共用。

## <a name="see-also"></a>另請參閱

[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)
