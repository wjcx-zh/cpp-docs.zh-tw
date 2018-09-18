---
title: 連結器工具錯誤 LNK1306 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1306
dev_langs:
- C++
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cc007a4a594c8593d7820365377f1c811b1e23c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050563"
---
# <a name="linker-tools-error-lnk1306"></a>連結器工具錯誤 LNK1306

> DLL 進入點函式不能管理;原生編譯

`DllMain` 無法編譯為 MSIL;它必須以原生編譯。

若要解決此問題，

- 包含進入點，而不需要將檔案編譯 **/clr**。

- 將項目點放`#pragma unmanaged`一節。

如需詳細資訊，請參閱:

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [managed、unmanaged](../../preprocessor/managed-unmanaged.md)

- [混合組件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)

- [DLL 和 Visual C++ 執行階段程式庫行為](../../build/run-time-library-behavior.md)

## <a name="example"></a>範例

下列範例會產生 LNK1306。

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

若要修正此問題，請勿使用 /clr 選項編譯這個檔案，或使用`#pragma`指示詞，以將項目點定義放在未受管理的一節，在此範例中所示：

```cpp
// LNK1306fix.cpp
// compile with: /clr /link /dll /entry:NewDllMain
#include <windows.h>
#pragma managed(push, off)
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
#pragma managed(pop)
```
