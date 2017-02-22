---
title: "使用擷取運算子 | Microsoft Docs"
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
  - ">> 運算子, 擷取運算子"
  - "擷取運算子"
  - "運算子 [C++], 擷取"
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用擷取運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

擷取運算子 \(`>>`\)，為所有標準 C\+\+ 資料型別預先編譯程序，最簡單的方式就是從輸入資料流物件取得位元組。  
  
 格式化文字輸入擷取運算子依賴分隔輸入資料值的插入空白像信號空間。  這並不方便，當文字欄位包含多個單字，或是當逗號分隔數字時。  在這個案例中，其中一種選擇是使用未格式化的輸入成員函式 [istream::getline](../Topic/basic_istream::getline.md) 讀取文字區塊包含空白字元，然後有特殊功能的區塊。  另一個方法會取得與 10% 成員函式的輸入資料流類別 \(例如 `GetNextToken`\)，可以呼叫 istream 成員擷取和格式字元資料。  
  
## 請參閱  
 [輸入資料流](../standard-library/input-streams.md)