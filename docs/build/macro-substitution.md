---
title: "巨集替換 | Microsoft Docs"
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
  - "NMAKE 程式, 巨集替換"
  - "NMAKE 中的替換巨集"
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 巨集替換
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當叫用了 *macroname* 後，*string2* 會取代其定義字串中 *string1* 的每個項目。  
  
## 語法  
  
```  
$(macroname:string1=string2)  
```  
  
## 備註  
 巨集替換區分大小寫且為常值，而 *string1* 和 *string2* 無法叫用巨集。  替換不修改原始定義。  您可以替換預先定義巨集中的任何文字，除了 [$$@](../build/filename-macros.md) 之外。  
  
 在冒號之前沒有空格或定位字元，而在冒號之後的任何空格或定位字元會被解譯為常值。  如果 *string2* 為 null，就會從巨集的定義字串中刪除 *string1* 的所有項目。  
  
## 請參閱  
 [使用 NMAKE 巨集](../build/using-an-nmake-macro.md)