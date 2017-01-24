---
title: "編譯器錯誤 C2940 | Microsoft Docs"
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
  - "C2940"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2940"
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2940
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': type\-class\-id 重複定義為區域 typedef  
  
 您無法使用泛型或範本類別作為本機 `typedef`。  
  
 下列範例會產生 C2940：  
  
```  
// C2940.cpp template<class T> struct TC {}; int main() { typedef int TC<int>;   // C2940 typedef int TC;   // OK }  
```  
  
 使用泛型時，也會發生 C2940：  
  
```  
// C2940b.cpp // compile with: /clr generic<class T> ref struct GC { }; int main() { typedef int GC<int>;   // C2940 typedef int GC; }  
```