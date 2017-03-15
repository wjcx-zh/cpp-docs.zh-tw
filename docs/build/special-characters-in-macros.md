---
title: "巨集中的特殊字元 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "特殊字元, NMAKE 巨集中"
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 巨集中的特殊字元
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在定義之後的數字符號 \(\#\) 會指定註解。  若要在巨集中指定常值數字符號，請使用插入號 \(^\)，如 ^\#。  
  
 貨幣符號 \($\) 會指定巨集引動過程。  若要指定常值 $，請使用 $$。  
  
 若要將定義延伸至新行，請以反斜線 \(\\\) 結束該行。  在叫用巨集時，會用空格取代反斜線和新行字元。  若要在行的結尾指定常值反斜線，請在常值反斜線之前加上插入號 \(^\)，或在之後加上註解規範 \(\#\)。  
  
 若要指定常值新行字元，請使用插入號 \(^\) 結束該行，如：  
  
```  
CMDS = cls^  
dir  
```  
  
## 請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)