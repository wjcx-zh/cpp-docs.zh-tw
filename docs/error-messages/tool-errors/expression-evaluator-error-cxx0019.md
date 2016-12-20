---
title: "運算式評估工具錯誤 CXX0019 | Microsoft Docs"
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
  - "CXX0019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0019"
  - "CXX0019"
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算式評估工具錯誤 CXX0019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

型別轉換錯誤  
  
 C 運算式評估工具無法如所撰寫般地執行型別轉換 \(Type Cast\)。  
  
 此錯誤與 CAN0019 相同。  
  
### 若要修正，請檢查下列可能原因  
  
1.  指定的型別是未知的型別。  
  
2.  指標型別 \(Pointer Type\) 的層級太多。  例如，型別轉換  
  
    ```  
    (char **)h_message  
    ```  
  
     無法由 C 運算式工具評估。