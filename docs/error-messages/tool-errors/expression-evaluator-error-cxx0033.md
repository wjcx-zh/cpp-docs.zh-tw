---
title: "運算式評估工具錯誤 CXX0033 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0033"
  - "CXX0033"
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算式評估工具錯誤 CXX0033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OMF 型別資訊發生錯誤  
  
 可執行檔沒有進行偵錯的有效目的模組格式 \(Object Module Format，OMF\)。  
  
 此錯誤與 CAN0033 相同。  
  
### 若要修正，請檢查下列可能原因  
  
1.  可執行檔不是以此版本 Visual C\+\+ 的連結器 \(Linker\) 所建立。  利用目前 LINK.exe 的版本重新連結目的碼 \(Object Code\)。  
  
2.  .exe 檔案可能已損毀。  重新編譯並連結此程式。