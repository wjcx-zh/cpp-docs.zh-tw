---
title: 資源編譯器錯誤 RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 4d298cdd9d96c55f283ce7f0e2ba04dd664941f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584609"
---
# <a name="resource-compiler-error-rw2001"></a>資源編譯器錯誤 RW2001

無效的指示詞在前置處理過的 RC 檔

RC 檔包含 **#pragma**指示詞。

使用 **#ifndef**使用的前置處理器指示詞**RC_INVOKED**常數資源編譯器定義當它處理的 include 檔案。 地方 **#pragma**指示詞的不是程式碼區塊中處理的時機**RC_INVOKED**常數定義。 只能由 C/c + + 編譯器，而不是由資源編譯器處理區塊中的程式碼。 下列程式碼範例會示範這項技術：

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**前置處理器指示詞沒有任何意義。RC 檔。 **#Include**中經常使用前置處理器指示詞。RC 包含標頭檔 （專案為基礎的自訂標頭檔或使用其中一個產品，Microsoft 所提供的標準標頭檔） 檔案。 其中包含檔案包含 **#pragma**指示詞。 由於標頭檔可包含一或多個其他標頭檔，檔案，其中包含違規 **#pragma**指示詞不會立即顯現。

**#Ifndef RC_INVOKED**技巧可以控制包括專案為基礎的標頭檔中的標頭檔。