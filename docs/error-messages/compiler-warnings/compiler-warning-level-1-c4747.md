---
title: 編譯器警告（層級1） C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: 623b29d345a850cc312f23e4c521aa0be5b47242
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052435"
---
# <a name="compiler-warning-level-1-c4747"></a>編譯器警告（層級1） C4747

呼叫受控的 ' entrypoint '： Managed 程式碼可能無法在載入器鎖定下執行，包括 DLL 進入點和從 DLL 進入點到達的呼叫

編譯器發現編譯為 MSIL 的（可能） DLL 進入點。  由於載入已編譯為 MSIL 的 DLL 的潛在問題，因此強烈建議您不要將 DLL 進入點函式編譯為 MSIL。

如需詳細資訊，請參閱[初始化混合元件](../../dotnet/initialization-of-mixed-assemblies.md)和[連結器工具錯誤 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請勿使用 **/clr**編譯模組。

1. 使用 `#pragma unmanaged`標記進入點函式。

## <a name="example"></a>範例

下列範例會產生 C4747。

```cpp
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```