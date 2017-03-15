---
title: "使用不帶 () 的函式名稱不會產生程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "函式 [C++], 不包含括號"
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用不帶 () 的函式名稱不會產生程式碼
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當程式中宣告的函式名稱在使用時沒有加上括號，編譯器 \(Compiler\) 便不會產生程式碼。  無論該函式是否帶參數，都會發生這種情況，因為編譯器會計算函式的位址；不過，由於沒有出現函式呼叫 \(Function Call\) 運算子 "\(\)"，因此不會進行任何呼叫。  這種結果類似下式：  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 在 Visual C\+\+ 中，即使使用警告等級 4 也不會產生診斷輸出。  不會發出任何警告；不會產生任何程式碼。  
  
 以下的示範程式碼會正確無誤地編譯 \(在警告下\) 並連結，但不會產生 `funcn( )` 參考的任何程式碼。  若要正確執行，請加入函式呼叫運算子 "\(\)"。  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## 請參閱  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)