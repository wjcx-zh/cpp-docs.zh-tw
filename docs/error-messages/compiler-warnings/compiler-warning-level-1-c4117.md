---
title: "編譯器警告 (層級 1) C4117 | Microsoft Docs"
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
  - "C4117"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4117"
ms.assetid: c45aa281-4cc1-4dfd-bd32-bd7a60ddd577
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4117
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

巨集名稱 'name' 為保留字; 忽略 'Command'  
  
### 透過檢查下列可能原因進行修正  
  
1.  嘗試定義或取消定義預先定義的巨集。  
  
2.  嘗試定義或取消定義前置處理器運算子 **defined**。  
  
 下列範例會產生 C4117：  
  
```  
// C4117.cpp // compile with: /W1 #define __FILE__ test         // C4117. __FILE__ is a predefined macro #define ValidMacroName test   // ok int main() { }  
```