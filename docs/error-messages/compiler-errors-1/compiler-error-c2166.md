---
title: "編譯器錯誤 C2166 | Microsoft Docs"
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
  - "C2166"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2166"
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2166
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

左值 \(l\-value\) 指定 const 物件  
  
 程式碼嘗試修改宣告為 `const` 的項目。  
  
 下列範例會產生 C2166：  
  
```  
// C2166.cpp int f(); int main() { ( (const int&) 1 ) = 5;   // C2166 }  
```