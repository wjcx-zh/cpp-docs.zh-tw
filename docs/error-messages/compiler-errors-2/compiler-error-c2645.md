---
title: "編譯器錯誤 C2645 | Microsoft Docs"
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
  - "C2645"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2645"
ms.assetid: 6609c2fa-c3b2-4a6b-8e8d-58fb52f67175
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2645
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

成員的指標沒有限定名稱 \(找到 ':: \*'\)  
  
 成員指標的宣告未指定類別。  
  
 下列範例會產生 C2645：  
  
```  
// C2645.cpp  
class A {};  
int main() {  
   int B::* bp;   // C2645 B not defined  
   int A::* ap;   // OK  
}  
```