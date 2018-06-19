---
title: 編譯器警告 （層級 1） C4747 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 203943f3741d07e278652a7032a6dcdcb305a384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285820"
---
# <a name="compiler-warning-level-1-c4747"></a>編譯器警告 (層級 1) C4747
呼叫 managed '進入點': Managed 程式碼不會執行載入器鎖定，包括 DLL 進入點和從 DLL 進入點到達的呼叫下  
  
 編譯器發現 （可能） 的 DLL 進入點，編譯為 MSIL。  載入的 DLL 的進入點已經編譯為 MSIL 的潛在問題，因為您會強烈建議您不要從編譯為 MSIL DLL 進入點函式。  
  
 如需詳細資訊，請參閱[初始化的混合的組件](../../dotnet/initialization-of-mixed-assemblies.md)和[連結器工具錯誤 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  無法編譯的模組 **/clr**。  
  
2.  將進入點函式，以標示`#pragma unmanaged`。  
  
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