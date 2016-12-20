---
title: "編譯器錯誤 C2800 | Microsoft Docs"
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
  - "C2800"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2800"
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2800
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operator' : 不可以多載  
  
 下列運算子不可以進行多載：類別 \(Class\) 成員存取 \(`.`\)、成員指標 \(`.*`\)、範圍解析 \(`::`\)、條件運算式 \(`? :`\) 和 `sizeof`。  
  
 下列範例會產生 C2800：  
  
```  
// C2800.cpp  
// compile with: /c  
class C {  
   operator:: ();   // C2800  
};  
```