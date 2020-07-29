---
title: 必要和選擇性標頭檔
ms.date: 11/04/2016
f1_keywords:
- c.headers
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
ms.openlocfilehash: 8d1547ae7dd3b6adb33271e93e85022f04859886
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211602"
---
# <a name="required-and-optional-header-files"></a>必要和選擇性標頭檔

每個執行階段常式的描述都包含一個清單，列出該常式必要和選擇性的 Include (或標頭 (.H)) 檔案。 必須包含必要的標頭檔以取得常式的函式宣告，或是由另一個於內部呼叫的常式所使用的定義。 選擇性標頭檔通常會包含以利用預先定義的常數、類型定義或內嵌巨集。 下表列出一些選擇性標頭檔內容的範例：

|定義|範例|
|----------------|-------------|
|巨集定義|如果程式庫常式是實作為巨集，則巨集定義可能位於不是原始常式標頭檔的其他標頭檔中。 例如，`_toupper` 巨集是在 CTYPE.H 標頭檔中定義，而函式 `toupper` 則是在 STDLIB.H 中宣告。|
|預先定義的常數|許多程式庫常式會參考於標頭檔中定義的常數。 例如，`_open` 常式會使用如 `_O_CREAT` 的常數，此常數是在標頭檔 FCNTL.H 中定義。|
|類型定義|某些程式庫常式會以引數的形式傳回結構或接受結構。 例如，資料流輸入/輸出常式使用 `FILE` 類型的結構，它是在 STDIO.H 中定義。|

執行階段程式庫標頭檔會以 ANSI/ISO C 標準的建議樣式提供函式宣告。 編譯器會針對在和常式參考相關聯的函式宣告之後發生的任何常式參考執行類型檢查。 函式宣告對於傳回某種類型的值 **`int`** （預設為）的常式而言特別重要。 當常式未在其宣告中指定適當的傳回值時，編譯器會將其視為傳回 **`int`** ，這可能會造成非預期的結果。 如需詳細資訊，請參閱[類型檢查](../c-runtime-library/type-checking-crt.md)。

## <a name="see-also"></a>另請參閱

[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
