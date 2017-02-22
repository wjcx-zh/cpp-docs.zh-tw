---
title: "編譯器錯誤 C2657 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2657"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2657"
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2657
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在陳述式開頭找到 'class::\*' \(是否忘記指定型別?\)  
  
 這行以成員指標識別項開頭。  
  
 造成這項錯誤的原因可能是：在成員指標的宣告中遺漏型別規範。  
  
 下列範例會產生 C2657：  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```