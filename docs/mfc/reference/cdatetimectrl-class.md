---
title: "CDateTimeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDateTimeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl class"
  - "date-picking functionality"
  - "DateTimePicker control [MFC]"
  - "DateTimePicker control [MFC], CDateTimeCtrl class"
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDateTimeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝、日期時間選擇器控制項的功能。  
  
## 語法  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDateTimeCtrl::CDateTimeCtrl](../Topic/CDateTimeCtrl::CDateTimeCtrl.md)|建構 `CDateTimeCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDateTimeCtrl::CloseMonthCal](../Topic/CDateTimeCtrl::CloseMonthCal.md)|結束目前的日期和時間選擇器控制項。|  
|[CDateTimeCtrl::Create](../Topic/CDateTimeCtrl::Create.md)|建立日期時間選擇器控制項並將其附加至 `CDateTimeCtrl` 物件。|  
|[CDateTimeCtrl::GetDateTimePickerInfo](../Topic/CDateTimeCtrl::GetDateTimePickerInfo.md)|擷取與目前的日期和時間選擇器控制項的資訊。|  
|[CDateTimeCtrl::GetIdealSize](../Topic/CDateTimeCtrl::GetIdealSize.md)|傳回使用顯示目前日期或時間、日期時間選擇器控制項最適合的大小。|  
|[CDateTimeCtrl::GetMonthCalColor](../Topic/CDateTimeCtrl::GetMonthCalColor.md)|擷取月曆的特定部分的色彩在日期時間選擇器控制項內。|  
|[CDateTimeCtrl::GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md)|擷取 `CMonthCalCtrl` 物件與日期時間選擇器控制項。|  
|[CDateTimeCtrl::GetMonthCalFont](../Topic/CDateTimeCtrl::GetMonthCalFont.md)|擷取日期時間選擇器控制項子月曆控制項中目前所使用的字型。|  
|[CDateTimeCtrl::GetMonthCalStyle](../Topic/CDateTimeCtrl::GetMonthCalStyle.md)|取得目前的日期和時間選擇器控制項的樣式。|  
|[CDateTimeCtrl::GetRange](../Topic/CDateTimeCtrl::GetRange.md)|擷取目前最小和最大容許系統時間的日期時間選擇器控制項。|  
|[CDateTimeCtrl::GetTime](../Topic/CDateTimeCtrl::GetTime.md)|從日期時間選擇器控制項在指定的 `SYSTEMTIME` 結構擷取目前選取的時間來放置。|  
|[CDateTimeCtrl::SetFormat](../Topic/CDateTimeCtrl::SetFormat.md)|設定日期時間選擇器控制項顯示具有指定格式字串符合。|  
|[CDateTimeCtrl::SetMonthCalColor](../Topic/CDateTimeCtrl::SetMonthCalColor.md)|設定月曆的特定部分的色彩在日期時間選擇器控制項內。|  
|[CDateTimeCtrl::SetMonthCalFont](../Topic/CDateTimeCtrl::SetMonthCalFont.md)|設定日期時間選擇器控制項子月曆控制項上的字型。|  
|[CDateTimeCtrl::SetMonthCalStyle](../Topic/CDateTimeCtrl::SetMonthCalStyle.md)|設定目前的日期和時間選擇器控制項的樣式。|  
|[CDateTimeCtrl::SetRange](../Topic/CDateTimeCtrl::SetRange.md)|設定的最小和最大容許系統時間的日期時間選擇器控制項。|  
|[CDateTimeCtrl::SetTime](../Topic/CDateTimeCtrl::SetTime.md)|設定日期時間選擇器控制項的時間。|  
  
## 備註  
 日期時間選擇器控制項 DTP \(控制項\) 提供簡單的介面交換日期和時間資訊與使用者。  這個介面包含欄位，每一個會顯示在控制項中儲存日期和時間資訊的一部分。  使用者可以在控制項中儲存的資訊可以變更字串內容在特定欄位。  使用滑鼠或鍵盤，使用者可以從欄位移動至欄位。  
  
 您可以套用各種樣式自訂日期時間選擇器控制項加入至物件，當您建立套件時。  請參閱在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 的 [日期時間選擇器控制項模式。](http://msdn.microsoft.com/library/windows/desktop/bb761728) 如需樣式的詳細資訊的特定日期時間選擇器控制項。  使用格式模式，您可以設定 DTP 控制項的顯示格式。  這些格式模式在 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 主題所述 [日期時間選擇器控制項模式。](http://msdn.microsoft.com/library/windows/desktop/bb761728)「格式下樣式」。  
  
 日期時間選擇器控制項也使用告知和回呼，在 [使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)說明。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## 需求  
 **Header:** afxdtctl.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL1](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl Class](../../mfc/reference/cmonthcalctrl-class.md)