---
title: "編譯器警告 （層級 1） C4532 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4532
dev_langs: C++
helpviewer_keywords: C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5cec2f70dfa6781c237cc1c08079904c7b48e171
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4532"></a>編譯器警告 (層級 1) C4532
'continue': 跳出 __finally/finally 區塊有未定義的行為在終止處理期間  
  
 編譯器遇到下列關鍵字：  
  
-   [continue](../../cpp/continue-statement-cpp.md)  
  
-   [break](../../cpp/break-statement-cpp.md)  
  
-   [goto](../../cpp/goto-statement-cpp.md)  
  
 造成出的跳躍點[__finally](../../cpp/try-finally-statement.md)或[最後](../../dotnet/finally.md)異常終止期間的區塊。  
  
 如果發生例外狀況，且在堆疊回溯終止處理常式執行期間 (`__finally`或 finally 區塊)，和您的程式碼跳出`__finally`之前封鎖`__finally`區塊結束時，行為是未定義。 控制項不會傳回回溯程式碼，因此可能未正確處理例外狀況。  
  
 如果您必須跳出**__finally**封鎖，請先檢查異常終止。  
  
 下列範例會產生 C4532;只是標記為註解的跳躍陳述式，以解決的警告。  
  
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