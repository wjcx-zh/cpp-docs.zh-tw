---
title: 編譯器錯誤 C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: 14969c9cdf4b00844d2001bf4817ea7ffc9bfba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662927"
---
# <a name="compiler-error-c2011"></a>編譯器錯誤 C2011

'identifier': 'type' 類型重複定義

識別項已定義為 `type`。 檢查識別項是否重複定義。

如果您將標頭檔或類型庫多次匯入至相同檔案中，您也會收到 C2011。 若要避免多次包含標頭檔中定義的類型，使用 include 防護或`#pragma`[一旦](../../preprocessor/once.md)指示詞標頭檔。

如果您需要尋找重新定義的類型的初始宣告，您可以使用[/P](../../build/reference/p-preprocess-to-a-file.md)編譯器旗標，以產生前置處理過的輸出傳遞至編譯器。 您可以使用文字搜尋工具，在輸出檔中尋找重複定義的識別項的執行個體。

下列範例會產生 C2011，並示範修正此問題的方法：

```
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```