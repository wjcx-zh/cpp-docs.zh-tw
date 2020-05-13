---
title: 外部連結
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 35b0fda1f501755640123f5181454a5c36b7e986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233732"
---
# <a name="external-linkage"></a>外部連結

如果識別項在檔案範圍層級的第一個宣告未使用 **static** 儲存類別指定名稱，則物件會具有外部連結。

如果函式的識別項宣告沒有 *storage-class-specifier*，其連結的判斷方式會像是使用 *storage-class-specifier* `extern` 宣告一般。 如果物件的識別項宣告具有檔案範圍，但沒有 *storage-class-specifier*，表示其連結為外部連結。

具有外部連結的識別項名稱所指定的函式或資料物件，會與任何其他具有外部連結的相同名稱宣告所指定的函式或資料物件相同。 這兩種宣告可以位於相同轉譯單位或不同轉譯單位中。 如果物件或函式同時具有全域存留期，則物件或函式會由整個程式共用。

## <a name="see-also"></a>請參閱

[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)
