---
title: "運算式評估工具錯誤 CXX0036 | Microsoft Docs"
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
  - "CXX0036"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0036"
  - "CXX0036"
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算式評估工具錯誤 CXX0036
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

內容 {...} 規格錯誤  
  
 使用內容運算子 \(**{}**\) 所產生的數個錯誤其中一種，就可能會產生這個訊息。  
  
-   所給定的內容運算子 \(**{}**\) 語法不正確。  
  
     內容運算子的語法為：  
  
     {*function*,*module*,*dll*}*expression*  
  
     這會指定運算式的內容。  內容運算子和型別轉換具有相同的優先順序及用法。  
  
     後面的逗號可以省略。  如果任何函式、模組，或 *dll* 中包含常值逗號，您必須將整個名稱置於括弧內。  
  
-   函式名稱的拼字錯誤，或是函式名稱不存在於指定的模組或動態連結程式庫中。  
  
     由於 C 是會區分大小寫的語言，因此所指定的函式必須與來源定義的大小寫完全相符。  
  
-   找不到模組或 DLL。  
  
     檢查指定的模組或 DLL 的完整路徑名稱。  
  
 此錯誤與 CAN0036 相同。