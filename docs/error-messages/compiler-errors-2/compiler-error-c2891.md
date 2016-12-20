---
title: "編譯器錯誤 C2891 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2891"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2891"
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
caps.latest.revision: 7
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2891
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter' : 無法取得樣板參數的位址  
  
 不要使用如下的程式碼：  
  
```  
template <int i> int* f() { return &i; }  
```  
  
 請使用這個：  
  
```  
template <int i> int* f() { return i; }  
```