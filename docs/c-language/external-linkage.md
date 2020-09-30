---
title: 外部連結
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: d8a7655b7504aa8458bda8db24ff3f919b5b09c1
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509919"
---
# <a name="external-linkage"></a>外部連結

如果識別碼在檔案範圍層級的第一個宣告未使用 **`static`** 儲存類別指定名稱，則物件會具有外部連結。

如果函式的識別碼宣告沒有 *儲存類別*指定名稱，則其連結的判斷就如同使用 *儲存類別規範*來宣告一樣 **`extern`** 。 如果物件的識別項宣告具有檔案範圍，但沒有 *storage-class-specifier*，表示其連結為外部連結。

具有外部連結的識別項名稱所指定的函式或資料物件，會與任何其他具有外部連結的相同名稱宣告所指定的函式或資料物件相同。 這兩種宣告可以位於相同轉譯單位或不同轉譯單位中。 如果物件或函式同時具有全域存留期，則物件或函式會由整個程式共用。

## <a name="see-also"></a>另請參閱

[使用 extern 指定連結](../cpp/extern-cpp.md)
