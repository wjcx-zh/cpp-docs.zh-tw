---
title: "Current Time: Automation Classes | Microsoft Docs"
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
  - "Automation classes, 目前時間"
  - "目前時間, COleDateTime object"
  - "程序, getting current time"
  - "時間, getting current"
  - "時間, setting current"
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Current Time: Automation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程序說明如何建立 `COleDateTime` 物件並以目前的時間。  
  
#### 取得目前的時間  
  
1.  建立 `COleDateTime` 物件。  
  
2.  請呼叫 `GetCurrentTime`。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/CPP/current-time-automation-classes_1.cpp)]  
  
## 請參閱  
 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)