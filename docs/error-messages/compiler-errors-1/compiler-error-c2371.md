---
title: "編譯器錯誤 C2371 | Microsoft Docs"
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
  - "C2371"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2371"
ms.assetid: d383993d-05ef-4e35-8129-3b58a6f7b7b7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2371
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 重複定義；基本類型不相同  
  
 已宣告識別項。  
  
 下列範例會產生 C2371：  
  
```  
// C2371.cpp int main() { int i; float i;   // C2371, redefinition float f;   // OK }  
```