---
title: "輸入資料流操作工具 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "輸入資料流物件"
  - "輸入資料流, 操作工具"
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 輸入資料流操作工具
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

許多操作工具，例如 [setprecision](../Topic/setprecision.md)，為 `ios` 類別所定義和以套用至輸入資料流。  少量操作工具，不過，實際上會影響輸入資料流物件。  這些，最重要的基數操作工具、 `dec`、 `oct`和 `hex`，判斷轉換基底搭配數字輸入資料流。  
  
 在擷取， `hex` 操作工具啟用處理各種 XML 編碼格式。  例如， c、C\#、0xc、0xC、0Xc 和 0XC 是所有解譯為十進位整數 12。  除了 0 至 9，字母 A 到 F、a 到 f、x 和 X 以外的任何字元結束數值轉換。  因此 `"124n5"` 序列轉換為具有 [basic\_ios::fail](../Topic/basic_ios::fail.md) 位元集合的步驟 124。  
  
## 請參閱  
 [輸入資料流](../standard-library/input-streams.md)