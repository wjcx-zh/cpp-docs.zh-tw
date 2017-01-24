---
title: "managed、unmanaged | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.unmanaged"
  - "managed_CPP"
  - "unmanaged_CPP"
  - "vc-pragma.managed"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "managed pragma"
  - "Pragma, Managed"
  - "Pragma, Unmanaged"
  - "unmanaged pragma"
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# managed、unmanaged
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

啟用函式層級控制項，用於編譯 Managed 或 Unmanaged 的函式。  
  
## 語法  
  
```  
  
        #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## 備註  
 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項提供模組層級的控制項，可用於編譯 Managed 或 Unmanaged 的函式。  
  
 編譯 Unmanaged 函式用於原生平台，Common Language Runtime 會將該部分的程式執行傳遞至該原生平台。  
  
 預設會在使用 **\/clr** 時編譯 Unmanaged 函式。  
  
 套用這些 pragma 時：  
  
-   將 pragma 新增到函式之前而不是函式主體之內。  
  
-   將 pragma 新增到 `#include` 陳述式之後。  請勿在 `#include` 陳述式之前使用這些 pragma。  
  
 如果編譯時未使用 `managed`，編譯器會忽略 `unmanaged` 和 **\/clr** pragma。  
  
 具現化樣板函式時，定義樣板時的 pragma 狀態決定函式為 Managed 或 Unmanaged 函式。  
  
 如需詳細資訊，請參閱[混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)。  
  
## 範例  
  
```  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
  **In managed function.  In unmanaged function.**    
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)