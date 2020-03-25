---
title: 資源編譯器錯誤 RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: 900bfed9d57af0f6f5dd8fac19380bb7c382addc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190738"
---
# <a name="resource-compiler-error-rw2001"></a>資源編譯器錯誤 RW2001

前置處理的 RC 檔案中的指示詞無效

RC 檔案包含 **#pragma**指示詞。

搭配資源編譯器在處理 include 檔案時所定義的**RC_INVOKED**常數，使用 **#ifndef**預處理器指示詞。 將 **#pragma**指示詞放在定義**RC_INVOKED**常數時，不會處理的程式碼區塊內。 區塊中的程式碼只會由 C/C++編譯器處理，而不會由資源編譯器處理。 下列範例程式碼示範這項技術：

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**預處理器指示詞在中沒有任何意義。RC 檔案。 **#Include**預處理器指示詞在中經常使用。包含標頭檔的 RC 檔案（以專案為基礎的自訂標頭檔，或由 Microsoft 提供的標準標頭檔中的其中一項產品）。 其中一些包含檔案包含 **#pragma**指示詞。 因為標頭檔可以包含一或多個其他標頭檔，所以包含違規 **#pragma**指示詞的檔案可能不會立即明顯。

**#Ifndef RC_INVOKED**技術可以控制以專案為基礎的標頭檔中包含標頭檔。
