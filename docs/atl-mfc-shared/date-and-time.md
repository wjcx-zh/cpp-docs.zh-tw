---
title: "Date and Time | Microsoft Docs"
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
  - "日期, MFC"
  - "MFC, 日期和時間"
  - "時間"
  - "時間, MFC 程式設計"
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Date and Time
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 支援數種不同的方式使用日期和時間時使用。  這些需求包括：  
  
-   通用時間類別。  [CTime](../atl-mfc-shared/reference/ctime-class.md) 和 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) 類別封裝的大部分功能與 ANSI 標準時間程式庫，在 TIME.H. 宣告。  
  
-   支援系統時鐘。  MFC 3.0 版，支援加入至 Win32 `SYSTEMTIME` 和 `FILETIME` 資料型別的 `CTime` 。  
  
-   提供 [日期資料型別](../atl-mfc-shared/date-type.md)Automation 支援。  **DATE** 支援日期、時間和日期\/時間值。  [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 和 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 類別封裝了這項功能。  使用 Automation 支援，這些資料 [COleVariant](../mfc/reference/colevariant-class.md) 類別一起使用。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [日期和時間:一般用途類別](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
-   [日期和時間:SYSTEMTIME 支援](../atl-mfc-shared/date-and-time-systemtime-support.md)  
  
-   [日期和時間:Automation 支援](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [日期和時間:資料庫支援](../atl-mfc-shared/date-and-time-database-support.md)  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)