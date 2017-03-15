---
title: "__ud2 | Microsoft Docs"
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
  - "__ud2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "UD2 指令"
  - "內建 __ud2"
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __ud2
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生未定義的指令。  
  
## 語法  
  
```  
void __ud2();  
```  
  
## 備註  
 如果您執行的未定義的指令，處理器就會造成無效的 opcode 例外狀況。  
  
 `__ud2`函式相當於`UD2`機器指令，並僅適用於核心模式。  如需詳細資訊，搜尋的文件中，"Intel 架構軟體開發人員的手冊，磁碟區 2： 指令集參考，"在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)站台。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__ud2`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 範例  
 下列範例會執行未定義的指令，會引發例外狀況。  例外處理常式接著會從零到其中一個變更傳回的程式碼。  
  
```  
// __ud2_intrinsic.cpp  
#include <stdio.h>  
#include <intrin.h>  
#include <excpt.h>  
// compile with /EHa  
  
int main() {  
  
// Initialize the return code to 0.  
 int ret = 0;  
  
// Attempt to execute an undefined instruction.  
  printf("Before __ud2(). Return code = %d.\n", ret);  
  __try {   
  __ud2();   
  }  
  
// Catch any exceptions and set the return code to 1.  
  __except(EXCEPTION_EXECUTE_HANDLER){  
  printf("  In the exception handler.\n");  
  ret = 1;  
  }  
  
// Report the value of the return code.   
  printf("After __ud2().  Return code = %d.\n", ret);  
  return ret;  
}  
```  
  
  **之前 \_\_ud2\(\)。**  
 **傳回碼 \= 0。**  
 **在例外狀況處理常式。**  
 **後 \_\_ud2\(\)。**  
 **傳回碼 \= 1。**   
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)