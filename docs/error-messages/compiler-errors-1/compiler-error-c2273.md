---
title: "編譯器錯誤 C2273 | Microsoft Docs"
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
  - "C2273"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2273"
ms.assetid: 3c682c66-97bf-4a23-a22c-d9a26a92bf95
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2273
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 做為 '\>' 運算子的右邊是不合法的  
  
 `->` 運算子右側的運算元以型別形式出現。  
  
 這項錯誤可能是因嘗試存取使用者定義的型別轉換而產生。  在 \-\> 與 `type` 之間使用關鍵字 `operator`。  
  
 下列範例會產生 C2273：  
  
```  
// C2273.cpp  
struct MyClass {  
   operator int() {  
      return 0;  
   }  
};  
int main() {  
   MyClass * ClassPtr = new MyClass;  
   int i = ClassPtr->int();   // C2273  
   int j = ClassPtr-> operator int();   // OK  
}  
```