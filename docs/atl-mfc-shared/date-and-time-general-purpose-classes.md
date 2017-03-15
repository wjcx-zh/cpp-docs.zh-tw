---
title: "Date and Time: General-Purpose Classes | Microsoft Docs"
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
  - "date and time classes"
  - "time classes"
ms.assetid: b8115d7f-428a-4c41-9970-18502f2caca2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Date and Time: General-Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文件說明如何使用類別庫通用服務相關的日期和時間排列。  所描述的程序如下:  
  
-   [取得目前的時間](../atl-mfc-shared/current-time-general-purpose-classes.md)  
  
-   [計算已耗用時間。](../atl-mfc-shared/elapsed-time-general-purpose-classes.md)  
  
-   [格式化日期\/時間字串表示。](../atl-mfc-shared/formatting-time-values-general-purpose-classes.md)  
  
 `CTime` 類別提供輕鬆地表示日期和時間資訊。  `CTimeSpan` 類別表示已耗用時間，例如 `CTime` 兩個物件之間的差異。  
  
> [!NOTE]
>  CTime 的物件可以用來表示自 1970 年 1 月 1 日到 2038 年 1 月 18 日的日期。  `CTime` 物件具有解析度 1 秒。  `CTime` 根據 `time_t` 資料型別，定義在 *執行階段程式庫參考》中的*。  
  
## 請參閱  
 [Date and Time](../atl-mfc-shared/date-and-time.md)