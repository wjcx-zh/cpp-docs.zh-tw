---
title: "編譯器錯誤 C2097 | Microsoft Docs"
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
  - "C2097"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2097"
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2097
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不合法的初始化  
  
### 若要修正，請檢查下列可能原因  
  
1.  使用非常數的值來初始化一個變數。  
  
2.  使用長位址來初始化短位址。  
  
3.  在以 **\/Za** 編譯時，使用非常數的運算式來初始化區域結構、等位或陣列。  
  
4.  使用包含逗號運算子的運算式進行初始化。  
  
5.  使用不是常數也不是符號的運算式進行初始化。