---
title: "編譯器錯誤 C3470 | Microsoft Docs"
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
  - "C3470"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3470"
ms.assetid: 170c7a9d-214d-41b1-8f15-d4a4fc38aaa5
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3470
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 類別不能同時有索引子 \(預設索引的屬性\) 和運算子\[\]  
  
 類型無法定義預設索引子和運算子\[\]。  
  
## 範例  
 下列範例會產生 C3470：  
  
```  
// C3470.cpp // compile with: /clr using namespace System; ref class R { public: property int default[int] { int get(int i) { return i+1; } } int operator[](String^ s) { return Convert::ToInt32(s); }   // C3470 }; int main() { R ^ r = gcnew R; // return r[9] + r["32"] - 42; }  
```