---
title: "編譯器錯誤 C2048 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2048"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2048"
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C2048
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有一個以上的 default  
  
 `switch` 陳述式包含多個 `default` 標籤。 刪除其中一個 `default` 標籤，來解決這個錯誤。  
  
 下列範例會產生 C2048：  
  
```  
// C2048.cpp int main() { int a = 1; switch (a) { case 1: a = 0; default: a = 2; default:   // C2048 a = 3; } }  
```  
  
 可能的解決方式：  
  
```  
// C2048b.cpp int main() { int a = 1; switch (a) { case 1: a = 0; default: a = 2; } }  
```