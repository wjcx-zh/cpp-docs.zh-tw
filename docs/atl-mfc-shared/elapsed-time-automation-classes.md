---
title: "Elapsed Time: Automation Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Automation classes, 已耗用時間"
  - "calculating dates and times"
  - "計算, 日期和時間"
  - "日期, calculating intervals"
  - "已耗用時間, calculating in Automation"
  - "intervals, 日期和時間"
  - "時間, elapsed"
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Elapsed Time: Automation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個程序顯示如何計算兩個 `CTime` 物件之間的差異 `CTimeSpan` 並取得結果。  
  
#### 計算已耗用時間  
  
1.  建立兩個 `COleDateTime` 物件。  
  
2.  設定其中一個為目前時間的 `COleDateTime` 物件。  
  
3.  執行一些費時的工作。  
  
4.  設定為目前時間的另一 `COleDateTime` 物件。  
  
5.  採取這種區別兩個時間。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/CPP/elapsed-time-automation-classes_1.cpp)]  
  
## 請參閱  
 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)