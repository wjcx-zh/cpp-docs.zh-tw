---
title: "運算式評估工具錯誤 CXX0065 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0065"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0065"
  - "CXX0065"
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算式評估工具錯誤 CXX0065
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

變數必須有堆疊框架  
  
 運算式中包含存在於目前範圍內但還沒有被建立的變數。  
  
 當您逐步執行函式的初構但還沒有為函式建立堆疊框架 \(Stack Frame\)，或當您逐步執行到函式的結束代碼 \(Exit Code\) 時會發生此錯誤。  
  
 評估運算式前逐步執行初構程式碼 \(Prolog Code\)，直到建立堆疊框架為止。  
  
 此錯誤與 CAN0065 相同。