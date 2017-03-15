---
title: "連結器工具錯誤 LNK1306 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1306"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1306"
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 連結器工具錯誤 LNK1306
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

DLL 進入點 function 不可為 Managed，編譯為原生  
  
 DllMain 不能編譯成 MSIL；它必須編譯成原生。  
  
 若要解決這個問題，請執行下列動作：  
  
-   在不使用 **\/clr** 下，編譯包含進入點的檔案。  
  
-   將進入點放入 `#pragma unmanaged` 區段中。  
  
-   如需詳細資訊，請參閱  
  
-   [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [managed、unmanaged](../../preprocessor/managed-unmanaged.md)  
  
-   [混合組件的初始化](../../dotnet/initialization-of-mixed-assemblies.md)  
  
-   [執行階段程式庫行為](../../build/run-time-library-behavior.md)  
  
## 範例  
 下列範例會產生 LNK1306。  
  
```  
// LNK1306.cpp  
// compile with: /clr /link /dll /entry:NewDllMain  
// LNK1306 error expected  
#include <windows.h>  
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {  
   return 1;  
}  
```