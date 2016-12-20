---
title: "運算式評估工具錯誤 CXX0064 | Microsoft Docs"
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
  - "CXX0064"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0064"
  - "CXX0064"
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算式評估工具錯誤 CXX0064
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法在繫結虛擬成員函式上設定中斷點  
  
 在透過指標指向物件的虛擬成員函式上設定中斷點，例如：  
  
```  
pClass->vfunc( int );  
```  
  
 可輸入類別來在虛擬函式 \(Virtual Function\) 上設定中斷點，例如：  
  
```  
Class::vfunc( int );  
```  
  
 此錯誤與 CAN0064 相同。