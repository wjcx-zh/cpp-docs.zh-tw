---
title: "Current Time: General Purpose Classes | Microsoft Docs"
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
  - "目前時間, CTime object"
  - "初始化物件, with the current time"
  - "程序, getting current time"
  - "時間, getting current"
  - "時間, setting current"
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Current Time: General Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程序說明如何建立 `CTime` 物件並以目前的時間。  
  
#### 取得目前的時間  
  
1.  將一 `CTime` 物件，如下所示:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  未初始化的 `CTime` 物件不會初始化成為到期日。  
  
2.  呼叫 `CTime::GetCurrentTime` 函式從作業系統取得目前的時間。  這個函式會傳回可用來設定 `CTime`值的物件， `CTime` :  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_2.cpp)]  
  
     因為 `GetCurrentTime` 是從 `CTime` 類別的靜態成員函式，您必須限定其與類別和範圍解析運算子 \(`::`\)， `CTime::GetCurrentTime()`名稱的名稱。  
  
 當然，先前所列的兩個步驟可以合併成單一陳述式如下所示:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_3.cpp)]  
  
## 請參閱  
 [Date and Time: General\-Purpose Classes](../atl-mfc-shared/date-and-time-general-purpose-classes.md)