---
title: "編譯器警告 (層級 4) C4629 | Microsoft Docs"
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
  - "C4629"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4629"
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4629
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了雙拼詞，字元順序 'digraph' 被解譯為語彙基元 'char' \(如果這不是您想要的，請在兩個字元之間插入一個空格\)  
  
 在 [\/Za](../../build/reference/za-ze-disable-language-extensions.md) 下，偵測到雙拼詞時，編譯器會發出警告。  
  
 下列範例會產生 C4629：  
  
```  
// C4629.cpp // compile with: /Za /W4 int main() <%   // C4629 <% digraph for { }  
```