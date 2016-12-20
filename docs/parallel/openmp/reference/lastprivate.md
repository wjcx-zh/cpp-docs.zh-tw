---
title: "lastprivate | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "lastprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lastprivate OpenMP clause"
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lastprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定變數的封入內容的版本是等於最終的反覆項目 \(for 迴圈建構\) 或最後一個區段 \(\# pragma 區段\)，那麼無論哪一個執行緒會執行的私用版本。  
  
## 語法  
  
```  
lastprivate(var)  
```  
  
## 備註  
 其中，  
  
 `var`  
 為一組，那麼無論哪一個執行緒執行最終的反覆項目 \(for 迴圈建構\) 或最後一個區段 \(\# pragma 區段\) 的私用版本的變數。  
  
## 備註  
 `lastprivate`適用於下列指示詞：  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱 [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md)。  
  
## 範例  
 請參閱[schedule](../../../parallel/openmp/reference/schedule.md)的使用範例， `lastprivate`子句。  
  
## 請參閱  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)