---
title: "Elapsed Time: General-Purpose Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "adding dates"
  - "calculating dates and times"
  - "計算, 日期和時間"
  - "日期, calculating intervals"
  - "已耗用時間"
  - "已耗用時間, 計算"
  - "intervals, 日期和時間"
  - "時間, elapsed"
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Elapsed Time: General-Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程序顯示如何計算兩個 `CTime` 物件之間的差異 `CTimeSpan` 並取得結果。  
  
#### 計算已耗用時間  
  
1.  使用 `CTime` 和 `CTimeSpan` 物件計算已耗用時間，如下所示:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/CPP/elapsed-time-general-purpose-classes_1.cpp)]  
  
     一旦計算 `elapsedTime`，您可以使用 `CTimeSpan` 的成員函式擷取共用的時間值的元件。  
  
## 請參閱  
 [Date and Time: General\-Purpose Classes](../atl-mfc-shared/date-and-time-general-purpose-classes.md)