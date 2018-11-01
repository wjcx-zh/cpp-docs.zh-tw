---
title: 資源編譯器錯誤 RC2101
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 595e87b73d79a01993e0e9b3aaa814332b21413f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448018"
---
# <a name="resource-compiler-error-rc2101"></a>資源編譯器錯誤 RC2101

無效的指示詞在前置處理過的 RC 檔

資源編譯器檔案包含 **#pragma**指示詞。

使用 **#ifndef**與資源編譯器定義當它處理的 include 檔案的 RC_INVOKED 常數的前置處理器指示詞。 地方 **#pragma**指示詞的定義 RC_INVOKED 常數時，不會處理的程式碼區塊中。 只能由 C/c + + 編譯器，而不是由資源編譯器處理區塊中的程式碼。 下列程式碼範例會示範這項技術：

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**前置處理器指示詞沒有任何意義。RC 檔。 **#Include**中經常使用前置處理器指示詞。RC 包含標頭檔 （專案為基礎的自訂標頭檔或使用其中一個產品，Microsoft 所提供的標準標頭檔） 檔案。 其中包含檔案包含 **#pragma**指示詞。 由於標頭檔可包含一或多個其他標頭檔，檔案，其中包含違規 **#pragma**指示詞不會立即顯現。

**#Ifndef** RC_INVOKED 技巧可以控制包括專案為基礎的標頭檔中的標頭檔。