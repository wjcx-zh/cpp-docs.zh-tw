---
title: 內部連結
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 3709ca815877b98fe5dfe6e5b2eca6b5c627641b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229593"
---
# <a name="internal-linkage"></a>內部連結

如果物件或函式的檔案範圍識別碼宣告包含*儲存類別規範* **`static`** ，則識別碼具有內部連結。 否則，該識別項會具有外部連結。 如需 [storage-class-specifier](../c-language/c-storage-classes.md) 非終端項的討論，請參閱*儲存類別*。

在一個轉譯單位中，具有內部連結之識別項的每個執行個體表示相同的識別項或函式。 內部連結的識別項在轉譯單位中是唯一的。

## <a name="see-also"></a>另請參閱

[使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)
