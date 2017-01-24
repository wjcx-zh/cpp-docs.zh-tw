---
title: "編譯器警告 (層級 1) C4715 | Microsoft Docs"
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
  - "C4715"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4715"
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4715
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 不是所有控制路徑都傳回值  
  
 指定的函式可能不會傳回值。  
  
## 範例  
  
```  
// C4715a.cpp  
// compile with: /W1 /LD  
int func1( int i )  
{  
   if( i )  
   return 3;  // C4715 warning, nothing returned if i == 0  
}  
```  
  
 若要預防此警告，請修改程式碼，使所有路徑都有指派函式傳回值：  
  
```  
// C4715b.cpp  
// compile with: /LD  
int func1( int i )  
{  
   if( i ) return 3;  
   else return 0;     // OK, always returns a value  
}  
```  
  
 程式碼可能包含對永遠不會傳回之函式的呼叫，如下列範例所示：  
  
```  
// C4715c.cpp  
// compile with: /W1 /LD  
void fatal()  
{  
}  
int glue()  
{  
   if(0)  
      return 1;  
   else if(0)  
      return 0;  
   else  
      fatal();   // C4715  
}  
```  
  
 此程式碼也會產生警告，因為編譯器不知道 `fatal` 永遠不會返回。  若要避免程式碼產生錯誤訊息，請使用 [\_\_declspec\(noreturn\)](../../cpp/noreturn.md) 宣告 `fatal`。