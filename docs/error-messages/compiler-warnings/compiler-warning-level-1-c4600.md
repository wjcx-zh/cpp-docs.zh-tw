---
title: "編譯器警告 (層級 1) C4600 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4600"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4600"
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4600
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma 'macro name' : 必須是有效的非空字串  
  
 當您用 [pop\_macro](../../preprocessor/pop-macro.md) 或 [push\_macro](../../preprocessor/push-macro.md) 移除或推入巨集名稱時，不能指定空白字串。  
  
 下列範例會產生 C4600：  
  
```  
// C4600.cpp  
// compile with: /W1  
int main()  
{  
   #pragma push_macro("")   // C4600 passing an empty string  
}  
```