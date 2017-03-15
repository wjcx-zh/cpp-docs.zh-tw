---
title: "編譯器錯誤 C3286 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3286"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3286"
ms.assetid: 554328c8-cf44-4f7d-a8d2-def74d28ecdd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3286
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'specifier': 反覆運算變數不能有任何儲存類別規範  
  
 如需詳細資訊，請參閱 [\(NOTINBUILD\)儲存類別規範](http://msdn.microsoft.com/zh-tw/10b3d22d-cb40-450b-994b-08cf9a211b6c)。  
  
 如需詳細資訊，請參閱 [for each、in](../../dotnet/for-each-in.md)。  
  
## 範例  
 下列範例會產生 C3286：  
  
```  
// C3286.cpp // compile with: /clr int main() { array<int> ^p = { 1, 2, 3 }; for each (static int i in p) {}   // C3286 for each (int j in p) {}   // OK }  
```