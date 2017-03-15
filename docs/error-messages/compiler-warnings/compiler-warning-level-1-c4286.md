---
title: "編譯器警告 (層級 1) C4286 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4286"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4286"
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4286
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type1' : 由基底類別 \('type2'\) 攔截 \(第 number 行\)  
  
 指定的例外狀況 \(Exception\) 型別式由先前的處理器處理的。  第二個 catch 的型別衍生自第一個 catch 的型別。  基底類別的例外狀況會捕捉衍生類別的例外狀況。  
  
## 範例  
  
```  
//C4286.cpp  
// compile with: /W1  
#include <eh.h>  
class C {};  
class D : public  C {};  
int main()  
{  
    try  
    {  
        throw "ooops!";  
    }  
    catch( C ) {}  
    catch( D ) {}  // warning C4286, D is derived from C  
}  
```