---
title: "標準對話方塊資料交換常式 | Microsoft Docs"
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
  - "標準對話方塊, 資料交換常式"
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
caps.latest.revision: 13
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 標準對話方塊資料交換常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題列出在一般 MFC 對話方塊控制項的標準對話資料交換 \(Dialog Data Exchange，DDX\) 常式。  
  
> [!NOTE]
>  標準對話資料交換常式在標頭檔 afxdd\_.h. 定義。  然而，應用程式應包含 afxwin.h。  
  
### DDX 函式  
  
|||  
|-|-|  
|[DDX\_CBIndex](../Topic/DDX_CBIndex.md)|初始化或擷取下拉式方塊控制項中的目前選取項目的索引。|  
|[DDX\_CBString](../Topic/DDX_CBString.md)|初始化或擷取下拉式方塊控制項的編輯欄位的目前內容。|  
|[DDX\_CBStringExact](../Topic/DDX_CBStringExact.md)|初始化或擷取下拉式方塊控制項的編輯欄位的目前內容。|  
|[DDX\_Check](../Topic/DDX_Check.md)|初始化或擷取核取方塊控制項的目前狀態。|  
|[DDX\_Control](../Topic/DDX_Control.md)|子類別在對話方塊內的特定控制項。|  
|[DDX\_DateTimeCtrl](../Topic/DDX_DateTimeCtrl.md)|初始化或擷取日期時間選擇器控制項的日期和時間資料。|  
|[DDX\_IPAddress](../Topic/DDX_IPAddress.md)|初始化或擷取 IP 位址控制項的目前值。|  
|[DDX\_LBIndex](../Topic/DDX_LBIndex.md)|初始化或擷取清單方塊控制項中目前選取項目的索引。|  
|[DDX\_LBString](../Topic/DDX_LBString.md)|初始化或擷取清單方塊控制項中目前選取範圍。|  
|[DDX\_LBStringExact](../Topic/DDX_LBStringExact.md)|初始化或擷取清單方塊控制項中目前選取範圍。|  
|[DDX\_MonthCalCtrl](../Topic/DDX_MonthCalCtrl.md)|初始化或擷取月曆控制項的目前值。|  
|[DDX\_Radio](../Topic/DDX_Radio.md)|初始化或擷取在無線控制群組內目前正在檢查無線控制的以 0 起始的索引。|  
|[DDX\_Scroll](../Topic/DDX_Scroll.md)|初始化或擷取捲動控制項的捲動方塊的目前位置。|  
|[DDX\_Slider](../Topic/DDX_Slider.md)|初始化或擷取滑桿控制項的捲動方塊的目前位置。|  
|[DDX\_Text](../Topic/DDX_Text.md)|初始化或擷取編輯控制項的目前值。|  
  
## 請參閱  
 [標準對話資料驗證常式](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)