---
title: "編譯器錯誤 C3131 | Microsoft Docs"
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
  - "C3131"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3131"
ms.assetid: 38f20fac-83c9-4cd9-b7b5-74ca8f650ea6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3131
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

專案必須擁有 'module' 屬性搭配 'name' 屬性  
  
 [module](../../windows/module-cpp.md) 屬性必須有 name 參數。  
  
 下列範例會產生 C3131：  
  
```  
// C3131.cpp  
[emitidl];  
[module];   // C3131  
// try the following line instead  
// [module (name="MyLib")];  
  
[public]  
typedef long int LongInt;  
```