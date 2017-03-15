---
title: "運算式評估工具錯誤 CXX0017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0017"
  - "CXX0017"
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算式評估工具錯誤 CXX0017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到符號  
  
 找不到運算式中指定的符號。  
  
 造成此錯誤的原因可能是符號名稱的大小寫不符。  由於 C 和 C\+\+ 是會區分大小寫的語言，符號名稱必須與來源中定義的大小寫完全相同。  
  
 在偵錯時為監看變數而試著轉換變數的型別時，也會發生此錯誤。  `typedef` 可以宣告型別的新名稱，但是並不會定義新型別。  在偵錯工具中試圖轉換型別時，必須使用已定義的型別名稱。  
  
 此錯誤與 CAN0017 相同。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  確定程式中的符號在使用前都已經過宣告。  
  
2.  在偵錯工具中使用真正的型別名稱轉換變數，而不是使用 `typedef` 定義的名稱。