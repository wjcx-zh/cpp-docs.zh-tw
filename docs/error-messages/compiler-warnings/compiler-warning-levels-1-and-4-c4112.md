---
title: "編譯器警告 (層級 1 和 4) C4112 | Microsoft Docs"
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
  - "C4112"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4112"
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1 和 4) C4112
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#line 必須有介於 1 和數字間的整數  
  
 [\#line](../../preprocessor/hash-line-directive-c-cpp.md) 指示詞會指定超過允許範圍的整數參數。  
  
 如果指定的參數小於 1，行計數器就會重設為 1。 如果指定的參數大於編譯器定義限制的*數字*，行計數器不會變更。 這是 ANSI 相容性層級 1 警告 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 和具有 Microsoft 擴充功能的層級 4 警告 \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\)。  
  
 下列範例會產生 C4112：  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```