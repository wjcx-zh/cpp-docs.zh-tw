---
title: "編譯器警告 (層級 4) C4702 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4702"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4702"
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器警告 (層級 4) C4702
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不可能執行到的程式碼  
  
 這個警告是對 Visual Studio .NET 2003 的編譯器完成符合標準處理後的結果：不可能執行到的程式碼。  當編譯器 \(後端\) 偵測到有不可能執行到的程式碼時，它會產生屬於層級 4 警告的 C4702。  
  
 若要使程式碼在 Visual C\+\+ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本都有效，請移除不可能執行到的程式碼，或確定部分執行流程可執行到的所有原始程式碼是否正確。  
  
## 範例  
 下列範例會產生 C4702。  
  
```  
// C4702.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main() {  
   return 1;  
   printf_s("I won't print.\n");   // C4702 unreachable  
}  
```  
  
## 範例  
 以 **\/GX**、**\/EHc**、**\/EHsc** 或  **\/EHac** 編譯，並使用外部 C 函式時，程式碼可能會因為假設外部 C 函式不擲回而變得不可能執行到，因此使得攔截區塊不可能執行到。如果您覺得因為函式可以擲回而使得這個警告無效，請以 **\/EHa** 或 **\/EHs** 編譯，依例外狀況擲回而定。  
  
 如需詳細資訊，請參閱 [\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)。  
  
 下列範例會產生 C4702。  
  
```  
// C4702b.cpp  
// compile with: /W4 /EHsc  
#include <iostream>  
  
using namespace std;  
extern "C" __declspec(dllexport) void Function2(){}  
  
int main() {  
   try {  
      Function2();  
   }  
   catch (...) {  
      cout << "Exp: Function2!" << endl;   // C4702  
   }  
}  
```