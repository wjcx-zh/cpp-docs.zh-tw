---
title: "編譯器錯誤 C2274 | Microsoft Docs"
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
  - "C2274"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2274"
ms.assetid: 8e874903-f499-45ef-8291-f821eee4cc1c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2274
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 當做 '.' 運算子的右邊不合法  
  
 成員存取 \(.\) 運算子右側的運算元是一個型別。  
  
 這項錯誤可能是因嘗試存取使用者定義的型別轉換而產生。  在句號和 `type` 之間使用關鍵字 `operator`。  
  
 下列範例會產生 C2286：  
  
```  
// C2274.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
  
int main() {  
   MyClass ClassName;  
   int i = ClassName.int();   // C2274  
   int j = ClassName.operator int();   // OK  
}  
```