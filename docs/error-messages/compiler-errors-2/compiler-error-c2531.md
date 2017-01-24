---
title: "編譯器錯誤 C2531 | Microsoft Docs"
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
  - "C2531"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2531"
ms.assetid: c49afe15-55f8-4dc8-ac01-bf653622a7db
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2531
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 位元欄位的參考不合法  
  
 不允許位元欄位 \(Bit Field\) 的參考。  
  
 下列範例會產生 C2531：  
  
```  
// C2531.cpp  
// compile with: /c  
class P {  
   int &b1 : 10;   // C2531  
   int b2 : 10;   // OK  
};  
```