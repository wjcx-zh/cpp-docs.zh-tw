---
title: "編譯器警告 (層級 4) C4100 | Microsoft Docs"
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
  - "C4100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4100"
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier'：未參考的型式參數  
  
 未在函式主體中參考此型式參數。  已忽略未參考的參數。  
  
 當程式碼在屬於基本類型之未參考的參數上呼叫解構函式時，也可能發出 C4100。這是 Visual C\+\+ 編譯器的限制。  
  
 下列範例會產生 C4100：  
  
```  
// C4100.cpp  
// compile with: /W4  
void func(int i) {   // C4100, delete the unreferenced parameter to  
                     //resolve the warning  
   // i;   // or, add a reference like this  
}  
  
int main()  
{  
   func(1);  
}  
```