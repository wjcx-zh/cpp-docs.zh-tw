---
title: 編譯器警告 (層級 4) C4233
ms.date: 10/25/2017
f1_keywords:
- C4233
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
ms.openlocfilehash: 361e00b7361aab51ea077d7e248503f3654e5e58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516515"
---
# <a name="compiler-warning-level-4-c4233"></a>編譯器警告 (層級 4) C4233

> 使用非標準擴充: '*關鍵字*' 只在 c + +，C 不支援的關鍵字

編譯器將原始程式碼編譯為 C，而不是 c + +，以及您使用只適用於 c + + 中的關鍵字。 編譯器會編譯為 C 原始程式檔如果來源檔案的副檔名為.c 或使用[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要將層級 4 警告問題 c4233，這行加入您的原始程式碼檔：

```cpp
#pragma warning(4:4233)
```
