---
title: "編譯器錯誤 C2467 | Microsoft Docs"
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
  - "C2467"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2467"
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2467
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

匿名 'user\-defined\-type' 的宣告不合法  
  
 宣告了巢狀的使用者定義型別。  在使用 ANSI 的相容性選項 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 來編譯 C 原始程式碼時，會發生此錯誤。  
  
 下列範例會產生 C2467：  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```