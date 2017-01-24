---
title: "編譯器錯誤 C2714 | Microsoft Docs"
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
  - "C2714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2714"
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不允許 \_\_alignof\(void\)  
  
 傳遞給運算子的值無效。  
  
 如需詳細資訊，請參閱[\_\_alignof 運算子](../../cpp/alignof-operator.md)。  
  
## 範例  
 下列範例會產生 C2714。  
  
```  
// C2714.cpp  
int main() {  
   return __alignof(void);   // C2714  
   return __alignof(char);   // OK  
}  
```