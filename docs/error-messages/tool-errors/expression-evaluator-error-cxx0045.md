---
title: "運算式評估工具錯誤 CXX0045 | Microsoft Docs"
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
  - "CXX0045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0045"
  - "CXX0045"
ms.assetid: 32181bc8-e79c-4ad7-a82f-47c62ec06d7d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算式評估工具錯誤 CXX0045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不是函式  
  
 程式中的符號帶有引數清單，但此符號並不是函式的名稱。  
  
## 範例  
  
```  
queue( alpha, beta )  
```  
  
 當 `queue`  不是函式時。  
  
 此錯誤與 CAN0045 相同。