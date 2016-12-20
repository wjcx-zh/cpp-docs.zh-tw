---
title: "編譯器錯誤 C2601 | Microsoft Docs"
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
  - "C2601"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2601"
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2601
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 區域函式定義不合法  
  
 程式碼嘗試在函式內定義函式。  
  
 或者，可能是 C2601 錯誤位置之前的原始程式碼中有太多額外的括號。  
  
 下列範例會產生 C2601：  
  
```  
// C2601.cpp  
int main() {  
   int i = 0;  
  
   void funcname(int j) {   // C2601  
      j++;  
   }  
}  
```