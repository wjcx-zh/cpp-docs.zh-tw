---
title: "使用 NMAKE 巨集 | Microsoft Docs"
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
  - "巨集, NMAKE"
  - "NMAKE 巨集, 使用"
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 NMAKE 巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用巨集，請依下列所示，將巨集的名稱放置在由貨幣符號 \($\) 帶頭的括號中。  
  
## 語法  
  
```  
$(macroname)  
```  
  
## 備註  
 不可以使用空格。  如果 *macroname* 為單一字元，括號就是選擇性的。  定義字串會取代 $\(*macroname*\)；Null 字串則會取代未定義的巨集。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [巨集替換](../build/macro-substitution.md)  
  
## 請參閱  
 [巨集和 NMAKE](../build/macros-and-nmake.md)