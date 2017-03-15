---
title: "編譯器警告 (層級 1) C4747 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4747"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4747"
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器警告 (層級 1) C4747
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 Managed 'entrypoint': Managed 程式碼不可在載入器鎖定下執行，包括 DLL 進入點和從 DLL 進入點到達的呼叫  
  
 編譯器發現 \(可攜式\) DLL 進入點已編譯成 MSIL。由於載入進入點已編譯成 MSIL 的 DLL 會有潛在問題，極力建議您，不要將 DLL 進入點函式編譯成 MSIL。  
  
 如需詳細資訊，請參閱[混合組件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)與[連結器工具錯誤 LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md)。  
  
### 更正這個錯誤  
  
1.  不要以 **\/clr** 編譯模組。  
  
2.  以 `#pragma unmanaged` 標示進入點函式。  
  
## 範例  
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