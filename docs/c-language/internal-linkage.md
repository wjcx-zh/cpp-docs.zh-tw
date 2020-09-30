---
title: 內部連結
ms.date: 11/04/2016
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
ms.openlocfilehash: 2871ee68b7ae880d6ec5c33ea69eb1bfcc3e284c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509898"
---
# <a name="internal-linkage"></a>內部連結

如果物件或函式的檔案範圍識別碼宣告包含 *儲存類別規範* **`static`** ，表示識別碼具有內部連結。 否則，該識別項會具有外部連結。 如需 [storage-class-specifier](../c-language/c-storage-classes.md) 非終端項的討論，請參閱*儲存類別*。

在一個轉譯單位中，具有內部連結之識別項的每個執行個體表示相同的識別項或函式。 內部連結的識別項在轉譯單位中是唯一的。

## <a name="see-also"></a>另請參閱

[使用 extern 指定連結](../cpp/extern-cpp.md)
