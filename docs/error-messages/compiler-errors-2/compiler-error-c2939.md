---
title: "編譯器錯誤 C2939 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2939"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2939"
ms.assetid: 455b050b-f2dc-4b5b-bd6a-e1f81d3d1644
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2939
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': type\-class\-id 重複定義為區域資料變數  
  
 您無法使用泛型或樣板類別作為區域資料變數。  
  
 此錯誤可能是大括弧不對稱所造成。  
  
 下列範例會產生 C2939：  
  
```  
// C2939.cpp template<class T> struct TC { }; int main() { int TC<int>;   // C2939 int TC;   // OK }  
```  
  
 使用泛型時，也會發生 C2939：  
  
```  
// C2939b.cpp // compile with: /clr generic<class T> ref struct GC { }; int main() { int GC<int>;   // C2939 int GC;   // OK }  
```