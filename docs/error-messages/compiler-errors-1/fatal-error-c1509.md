---
title: "嚴重錯誤 C1509 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1509"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1509"
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 嚴重錯誤 C1509
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制 : 函式 'function' 中的例外狀況處理常式狀態太多。請簡化函式  
  
 程式碼超過了例外狀況處理常式 \(Exception Handler\) 狀態的內部限制 \(32,768 個狀態\)。  
  
 最常發生的原因是：函式包含了使用者定義的類別變數 \(Class Variable\) 和算術運算子所組成的複雜運算式。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  指定暫存變數的通用子運算式以簡化運算式。  
  
2.  將函式分割成較小的函式。