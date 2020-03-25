---
title: 資源編譯器錯誤 RC2101
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 3fb576758e447c54e4ddfe7ddb024a1fd35a65f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191648"
---
# <a name="resource-compiler-error-rc2101"></a>資源編譯器錯誤 RC2101

前置處理的 RC 檔案中的指示詞無效

資源編譯器檔案包含 **#pragma**指示詞。

搭配資源編譯器在處理 include 檔案時所定義的 RC_INVOKED 常數，使用 **#ifndef**預處理器指示詞。 將 **#pragma**指示詞放在定義 RC_INVOKED 常數時，不會處理的程式碼區塊內。 區塊中的程式碼只會由 C/C++編譯器處理，而不會由資源編譯器處理。 下列範例程式碼示範這項技術：

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma**預處理器指示詞在中沒有任何意義。RC 檔案。 **#Include**預處理器指示詞在中經常使用。包含標頭檔的 RC 檔案（以專案為基礎的自訂標頭檔，或由 Microsoft 提供的標準標頭檔中的其中一項產品）。 其中一些包含檔案包含 **#pragma**指示詞。 因為標頭檔可以包含一或多個其他標頭檔，所以包含違規 **#pragma**指示詞的檔案可能不會立即明顯。

**#Ifndef** RC_INVOKED 技術可以控制以專案為基礎的標頭檔中包含標頭檔。
