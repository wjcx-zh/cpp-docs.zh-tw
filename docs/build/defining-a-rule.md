---
title: "定義規則 | Microsoft Docs"
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
  - "定義推斷規則"
  - "NMAKE 程式, 推斷規則"
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 定義規則
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*fromext* 表示相依檔案的副檔名，*toext* 則表示目標檔案的副檔名。  
  
```  
.fromext.toext:  
   commands  
```  
  
## 備註  
 副檔名不區分大小寫。  可以叫用巨集以表示 *fromext* 和 *toext*；在前置處理中會展開巨集。  在 *fromext* 之前的句號 \(.\) 必須出現在行的開頭。  冒號 \(:\) 之前有零或多個空格或定位字元。  後面可以只接著空格或定位字元、以分號 \(;\) 指定命令、以數字正負號 \(\#\) 指定註解，或新行字元。  不可以使用其他空格。  在描述區塊中會指定命令。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [在規則中搜尋路徑](../build/search-paths-in-rules.md)  
  
## 請參閱  
 [推斷規則](../build/inference-rules.md)