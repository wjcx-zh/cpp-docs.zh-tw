---
title: "編譯器警告 (層級 1) C4532 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4532"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4532"
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4532
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'continue' : 跳出 \_\_finally\/finally 區塊在終止處理期間有未定義的行為  
  
 編譯器遇到下列關鍵字之一：  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 造成在異常終結期間，跳出 [\_\_finally](../../cpp/try-finally-statement.md) 或 [finally](../../dotnet/finally.md) 區塊。  
  
 如果發生例外狀況，同時堆疊在終結處理常式 \(`__finally` 或 finally 區塊\) 執行期間正進行回溯，而您的程式碼在 `__finally` 區塊結束之前即跳出 `__finally` 區塊，這種行為並未定義。  控制項無法回到復原程式碼，因此例外狀況可能無法正確地處理。  
  
 如果您必須跳出 **\_\_finally** 區段，請先檢查異常性終止。  
  
 下列範例會產生 C4532；只要將跳躍陳述式標示為註解即可解決該警告。  
  
```  
// C4532.cpp  
// compile with: /W1  
// C4532 expected  
int main() {  
   int i;  
   for (i = 0; i < 10; i++) {  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         continue;  
      }  
  
      __try {  
      } __finally {  
         // Delete the following line to resolve.  
         break;  
      }  
   }  
}  
```