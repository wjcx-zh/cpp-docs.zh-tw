---
title: "編譯器警告 （層級 1） C4747 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4747
dev_langs: C++
helpviewer_keywords: C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 094576ec19582b640ba0d4c57dfa34593177a267
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4747"></a>編譯器警告 (層級 1) C4747
呼叫 managed '進入點': Managed 程式碼不會執行載入器鎖定，包括 DLL 進入點和從 DLL 進入點到達的呼叫下  
  
 編譯器發現 （可能） 的 DLL 進入點，編譯為 MSIL。  載入的 DLL 的進入點已經編譯為 MSIL 的潛在問題，因為您會強烈建議您不要從編譯為 MSIL DLL 進入點函式。  
  
 如需詳細資訊，請參閱[初始化的混合的組件](../../dotnet/initialization-of-mixed-assemblies.md)和[連結器工具錯誤 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  無法編譯的模組**/clr**。  
  
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