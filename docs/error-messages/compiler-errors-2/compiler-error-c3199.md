---
title: "編譯器錯誤 C3199 | Microsoft Docs"
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
  - "C3199"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3199"
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3199
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

浮點 pragma 使用方式無效: 非精確模式不支援例外狀況  
  
 [float\_control](../../preprocessor/float-control.md) pragma 是用來在 **\/fp:precise** 以外的 [\/fp](../../build/reference/fp-specify-floating-point-behavior.md) 設定之下，指定浮點例外狀況模型。  
  
 下列範例會產生 C3199：  
  
```  
// C3199.cpp  
// compile with: /fp:fast  
#pragma float_control(except, on)   // C3199  
```