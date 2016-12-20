---
title: "編譯器錯誤 C2879 | Microsoft Docs"
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
  - "C2879"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2879"
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2879
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 只有現有的命名空間可以由命名空間別名定義授與不同的名稱  
  
 您不能將[命名空間別名](../../misc/namespace-alias.md)建立為命名空間以外的符號。  
  
 下列範例會產生 C2879：  
  
```  
// C2879.cpp  
int main() {  
   int i;  
   namespace A = i;   // C2879 i is not a namespace  
}  
```