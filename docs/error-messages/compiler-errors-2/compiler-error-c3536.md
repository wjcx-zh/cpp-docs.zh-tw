---
title: "編譯器錯誤 C3536 | Microsoft Docs"
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
  - "C3536"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3536"
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3536
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol': 無法在初始化之前使用  
  
 指定的符號無法在初始化之前使用。  實際上，這表示變數無法用來初始化其本身。  
  
### 更正這個錯誤  
  
1.  不要以變數本身來初始化變數。  
  
## 範例  
 下列範例會產生 C3536 錯誤，因為每個變數都是以其本身來初始化的。  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## 請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)