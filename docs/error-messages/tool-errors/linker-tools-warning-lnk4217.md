---
title: 連結器工具警告 LNK4217
ms.date: 04/09/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: 3fcb806afa064a4f6d9c9c0680c617662a3b9a21
ms.sourcegitcommit: 0ad3f4517e64900a2702dd3d366586f9e2bce2c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477388"
---
# <a name="linker-tools-warning-lnk4217"></a>連結器工具警告 LNK4217

> 符號 '*符號*'中所定義的'*filename_1.obj*'匯入'*filename_2.obj*'在函式'*函式*'

[__declspec （dllimport)](../../cpp/dllexport-dllimport.md)即使已定義符號的物件檔案，在相同的映像中指定的符號。 移除`__declspec(dllimport)`修飾詞，以解決這個警告。

*符號*是映像中定義的符號名稱。 *函式*是正在匯入符號的函式。

當您使用編譯時，不會出現這個警告[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項。

如果您嘗試在一起，連結兩個模組，相反地，您應該編譯第二個模組的第一個模組匯入程式庫時，也會發生 LNK4217。

```cpp
// LNK4217.cpp
// compile with: /LD
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

然後，

```cpp
// LNK4217b.cpp
// compile with: /c
#include "windows.h"
__declspec(dllexport) void func(unsigned short*) {}
```

嘗試連結這兩個模組，會導致 LNK4217。 編譯第二個範例，其中含有匯入程式庫，若要解決的第一個範例。