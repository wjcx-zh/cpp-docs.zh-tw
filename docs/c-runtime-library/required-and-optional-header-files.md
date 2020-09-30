---
title: 必要和選擇性標頭檔
description: 何時使用 Microsoft C 執行時間程式庫中的必要和選擇性標頭檔。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.headers
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
ms.openlocfilehash: 79a45aaba5e2872b23e70f3fd276d6f3cae11167
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589805"
---
# <a name="required-and-optional-header-files"></a>必要和選擇性標頭檔

每個執行階段常式的描述都包含一個清單，列出該常式必要和選擇性的 Include (或標頭 (.H)) 檔案。 必須包含必要的標頭檔以取得常式的函式宣告，或是由另一個於內部呼叫的常式所使用的定義。 選擇性標頭檔通常會包含以利用預先定義的常數、類型定義或內嵌巨集。 下表列出一些選擇性標頭檔內容的範例：

|定義|範例|
|----------------|-------------|
|巨集定義|如果程式庫常式是實作為巨集，則巨集定義可能位於不是原始常式標頭檔的其他標頭檔中。 例如，`_toupper` 巨集是在 CTYPE.H 標頭檔中定義，而函式 `toupper` 則是在 STDLIB.H 中宣告。|
|預先定義的常數|許多程式庫常式會參考於標頭檔中定義的常數。 例如，`_open` 常式會使用如 `_O_CREAT` 的常數，此常數是在標頭檔 FCNTL.H 中定義。|
|類型定義|某些程式庫常式會以引數的形式傳回結構或接受結構。 例如，資料流輸入/輸出常式使用 `FILE` 類型的結構，它是在 STDIO.H 中定義。|

執行階段程式庫標頭檔會以 ANSI/ISO C 標準的建議樣式提供函式宣告。 編譯器會針對在和常式參考相關聯的函式宣告之後發生的任何常式參考執行類型檢查。 函式宣告對於傳回某些類型（預設值除外）值的常式而言特別重要 **`int`** 。 編譯器不會在其宣告中指定適當的傳回值，因此編譯器會考慮傳回 **`int`** ，這可能會導致非預期的結果。 如需詳細資訊，請參閱[類型檢查](../c-runtime-library/type-checking-crt.md)。

## <a name="see-also"></a>另請參閱

[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)
