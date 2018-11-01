---
title: 連結器工具警告 LNK4217
ms.date: 11/04/2016
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 12766241832d39f0b47ed85036c0ebeb0447fc75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448044"
---
# <a name="linker-tools-warning-lnk4217"></a>連結器工具警告 LNK4217

本機定義的符號 'symbol' 函式 'function' 中匯入

[__declspec （dllimport)](../../cpp/dllexport-dllimport.md)即使在本機定義的符號，符號已指定。 移除`__declspec`修飾詞，以解決這個警告。

`symbol` 是映像中定義的符號名稱。 `function` 是正在匯入符號函式。

當您使用選項編譯時，不會出現此警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)。

如果您嘗試在一起，連結兩個模組，相反地，您應該編譯第二個模組的第一個模組匯入程式庫時，也會發生 LNK4217。

```
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

然後，

```
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

嘗試連結這兩個模組，將會導致 LNK4217，編譯第二個範例，其中含有匯入程式庫，若要解決的第一個範例。