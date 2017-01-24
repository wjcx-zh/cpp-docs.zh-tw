---
title: "標準對話方塊資料驗證常式 | Microsoft Docs"
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
  - "標準對話方塊, 資料驗證常式"
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
caps.latest.revision: 13
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 標準對話方塊資料驗證常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題列出在一般 MFC 對話方塊控制項使用的標準對話資料驗證 \(DDV\) 常式。  
  
> [!NOTE]
>  標準對話資料交換常式定義在標頭檔 afxdd\_.h。  然而，應用程式應包含 afxwin.h。  
  
### DDV 函式  
  
|||  
|-|-|  
|[DDV\_MaxChars](../Topic/DDV_MaxChars.md)|驗證一個控制項的值中字元數不超過一個指定的最大值。|  
|[DDV\_MinMaxByte](../Topic/DDV_MinMaxByte.md)|驗證指定之控制項的值未超過一個指定的 **BYTE** 範圍。|  
|[DDV\_MinMaxDateTime](../Topic/DDV_MinMaxDateTime.md)|驗證指定之控制項的值未超過一個指定的時間範圍。|  
|[DDV\_MinMaxDouble](../Topic/DDV_MinMaxDouble.md)|驗證指定之控制項的值未超過一個指定的 **double** 範圍。|  
|[DDV\_MinMaxDWord](../Topic/DDV_MinMaxDWord.md)|驗證指定之控制項的值未超過一個指定的 **DWORD** 範圍。|  
|[DDV\_MinMaxFloat](../Topic/DDV_MinMaxFloat.md)|驗證指定之控制項的值未超過一個指定的 **float** 範圍。|  
|[DDV\_MinMaxInt](../Topic/DDV_MinMaxInt.md)|驗證指定之控制項的值未超過一個指定的 **int** 範圍。|  
|[DDV\_MinMaxLong](../Topic/DDV_MinMaxLong.md)|驗證指定之控制項的值未超過一個指定的 **long** 範圍。|  
|[DDV\_MinMaxLongLong](../Topic/DDV_MinMaxLongLong.md)|驗證指定之控制項的值未超過一個指定的 **LONGLONG** 範圍。|  
|[DDV\_MinMaxMonth](../Topic/DDV_MinMaxMonth.md)|驗證指定之控制項的值未超過一個指定的日期範圍。|  
|[DDV\_MinMaxShort](../Topic/DDV_MinMaxShort.md)|驗證指定之控制項的值未超過一個指定的 **short** 範圍。|  
|[DDV\_MinMaxSlider](../Topic/DDV_MinMaxSlider.md)|驗證特定滑桿控制項值落在指定範圍內。|  
|[DDV\_MinMaxUInt](../Topic/DDV_MinMaxUInt.md)|驗證指定之控制項的值未超過一個指定的 **UINT** 範圍。|  
|[DDV\_MinMaxULongLong](../Topic/DDV_MinMaxULongLong.md)|驗證指定之控制項的值未超過一個指定的 **ULONGLONG** 範圍。|  
  
## 請參閱  
 [標準對話方塊資料交換常式](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)