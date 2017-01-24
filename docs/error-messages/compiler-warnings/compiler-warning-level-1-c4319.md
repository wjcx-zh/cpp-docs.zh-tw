---
title: "編譯器警告 (層級 1) C4319 | Microsoft Docs"
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
  - "C4319"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4319"
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4319
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 零擴展 'type' 至更大的 'type'  
  
 ~ \(位元補充\) 運算子的結果不帶正負號，然後在其轉換為較大的類型時零擴充。  
  
 在下列範例中，~\(a\-1\) 評估為 32 位元不帶正負號的長運算式，然後由零擴充轉換為 64 位元。  這可能會導致非預期的作業結果。  
  
```  
// C4319.cpp  
// compile with: cl /W4 C4319.cpp  
int main() {  
   unsigned long a = 0;  
   unsigned long long q = 42;  
   q = q & ~(a - 1);    // C4319 expected  
}  
```