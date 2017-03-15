---
title: "編譯器錯誤 C3198 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3198"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3198"
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器錯誤 C3198
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

浮點 pragma 使用方式無效: fenv\_access pragma 只能在精確模式運作  
  
 [fenv\_access](../../preprocessor/fenv-access.md) pragma 是在**\/fp:precise** 以外的 [\/fp](../../build/reference/fp-specify-floating-point-behavior.md) 設定下使用。  
  
 下列範例會產生 C3198：  
  
```  
// C3198.cpp  
// compile with: /fp:fast  
#pragma fenv_access(on)   // C3198  
```