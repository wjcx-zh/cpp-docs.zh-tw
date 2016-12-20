---
title: "LOCAL (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Local"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LOCAL directive"
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# LOCAL (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 \[巨集內的第一個指示詞**本機**定義都是唯一的巨集的每個執行個體的標籤。  
  
## 語法  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## 備註  
 在 \[程序定義中的第二個指示詞 \(**程序**\)， **本機**建立的程序期間存在的堆疊式變數。  *標籤* 可能是簡單的變數或陣列，包含 *計數*項目。  
  
## 請參閱  
 [Directives Reference](../../assembler/masm/directives-reference.md)