---
title: "編譯器錯誤 C2229 | Microsoft Docs"
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
  - "C2229"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2229"
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2229
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

type 'identifier' 擁有大小為零的不合法陣列  
  
 結構或位元欄位 \(Bit Field\) 的成員包含並非最後成員而大小為零的陣列。  
  
 由於可以用大小為零的陣列做為結構的最後成員，因此配置結構時必須指定其大小。  
  
 如果大小為零的陣列不是結構的最後成員，編譯器就無法計算其餘欄位的位移 \(Offset\)。  
  
 下列範例會產生 C2229：  
  
```  
// C2229.cpp  
struct S {  
   int a[0];  // C2229  zero-sized array  
   int b[1];  
};  
  
struct S2 {  
   int a;  
   int b[0];  
};  
  
int main() {  
   // allocate 7 elements for b field  
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];  
   s2->b[6] = 100;  
}  
```