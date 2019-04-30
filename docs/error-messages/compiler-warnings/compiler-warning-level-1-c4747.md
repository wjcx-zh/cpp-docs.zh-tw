---
title: 編譯器警告 (層級 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: ecaabd482049771b1d3915470a2be7a52e36d361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404011"
---
# <a name="compiler-warning-level-1-c4747"></a>編譯器警告 (層級 1) C4747

呼叫受控 ' 進入點 ':Managed 程式碼可能不會執行載入器鎖定，包括 DLL 進入點和從 DLL 進入點到達的呼叫下

編譯器發現 （可能） 的 DLL 進入點，編譯為 MSIL。  載入的 DLL 的進入點已編譯為 MSIL 的潛在問題，因為您是強烈建議您不要從編譯為 MSIL DLL 進入點函式項目。

如需詳細資訊，請參閱 <<c0> [ 初始化混合組件](../../dotnet/initialization-of-mixed-assemblies.md)並[連結器工具錯誤 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 無法編譯的模組 **/clr**。

1. 將標記與進入點函式`#pragma unmanaged`。

## <a name="example"></a>範例

下列範例會產生 C4747。

```
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