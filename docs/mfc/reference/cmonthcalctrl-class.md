---
title: "CMonthCalCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMonthCalCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl class"
  - "通用控制項, Internet Explorer 4.0"
  - "Internet Explorer 4.0 common controls"
  - "month calendar controls"
  - "month calendar controls, CMonthCalCtrl class"
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMonthCalCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝月曆控制項的功能。  
  
## 語法  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMonthCalCtrl::CMonthCalCtrl](../Topic/CMonthCalCtrl::CMonthCalCtrl.md)|建構 `CMonthCalCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMonthCalCtrl::Create](../Topic/CMonthCalCtrl::Create.md)|建立月曆控制項並將其附加至 `CMonthCalCtrl` 物件。|  
|[CMonthCalCtrl::GetCalendarBorder](../Topic/CMonthCalCtrl::GetCalendarBorder.md)|擷取目前月曆控制項的框線寬度。|  
|[CMonthCalCtrl::GetCalendarCount](../Topic/CMonthCalCtrl::GetCalendarCount.md)|擷取目前月曆控制項中顯示的行事曆的數目。|  
|[CMonthCalCtrl::GetCalendarGridInfo](../Topic/CMonthCalCtrl::GetCalendarGridInfo.md)|擷取目前月曆控制項的資訊。|  
|[CMonthCalCtrl::GetCalID](../Topic/CMonthCalCtrl::GetCalID.md)|擷取目前月曆控制項的行事曆識別項。|  
|[CMonthCalCtrl::GetColor](../Topic/CMonthCalCtrl::GetColor.md)|取得月曆控制項的指定範圍的色彩。|  
|[CMonthCalCtrl::GetCurrentView](../Topic/CMonthCalCtrl::GetCurrentView.md)|擷取目前月曆控制項中目前顯示的檢視。|  
|[CMonthCalCtrl::GetCurSel](../Topic/CMonthCalCtrl::GetCurSel.md)|擷取系統時間所指定的目前選取的日期。|  
|[CMonthCalCtrl::GetFirstDayOfWeek](../Topic/CMonthCalCtrl::GetFirstDayOfWeek.md)|在日曆最左欄取得第一個顯示星期。|  
|[CMonthCalCtrl::GetMaxSelCount](../Topic/CMonthCalCtrl::GetMaxSelCount.md)|擷取在月曆控制項中選取日期的目前最大數目。|  
|[CMonthCalCtrl::GetMaxTodayWidth](../Topic/CMonthCalCtrl::GetMaxTodayWidth.md)|擷取最大寛度的「today」目前月曆控制項的字串。|  
|[CMonthCalCtrl::GetMinReqRect](../Topic/CMonthCalCtrl::GetMinReqRect.md)|在月曆控制項擷取要求的最小大小顯示完整月份。|  
|[CMonthCalCtrl::GetMonthDelta](../Topic/CMonthCalCtrl::GetMonthDelta.md)|擷取月曆控制項的捲動速率。|  
|[CMonthCalCtrl::GetMonthRange](../Topic/CMonthCalCtrl::GetMonthRange.md)|擷取表示月曆控制項中顯示的高和低程度的日期資訊。|  
|[CMonthCalCtrl::GetRange](../Topic/CMonthCalCtrl::GetRange.md)|擷取在月曆控制項和最大日期為目前的最小值。|  
|[CMonthCalCtrl::GetSelRange](../Topic/CMonthCalCtrl::GetSelRange.md)|擷取表示日期範圍的上限和下限的日期資訊目前選取的資料列索引。|  
|[CMonthCalCtrl::GetToday](../Topic/CMonthCalCtrl::GetToday.md)|針對做為「today」指定的日期擷取日期資訊月曆控制項。|  
|[CMonthCalCtrl::HitTest](../Topic/CMonthCalCtrl::HitTest.md)|判斷月曆控制項的哪個部分在畫面上的指定點。|  
|[CMonthCalCtrl::IsCenturyView](../Topic/CMonthCalCtrl::IsCenturyView.md)|指出目前的月曆控制項的目前檢視是否為世紀檢視。|  
|[CMonthCalCtrl::IsDecadeView](../Topic/CMonthCalCtrl::IsDecadeView.md)|指出目前的月曆控制項的目前檢視是否為十年中檢視。|  
|[CMonthCalCtrl::IsMonthView](../Topic/CMonthCalCtrl::IsMonthView.md)|指出目前的月曆控制項的目前檢視是否為月份檢視。|  
|[CMonthCalCtrl::IsYearView](../Topic/CMonthCalCtrl::IsYearView.md)|指出目前的月曆控制項的目前檢視是否為年檢視。|  
|[CMonthCalCtrl::SetCalendarBorder](../Topic/CMonthCalCtrl::SetCalendarBorder.md)|設定目前月曆控制項的框線寬度。|  
|[CMonthCalCtrl::SetCalendarBorderDefault](../Topic/CMonthCalCtrl::SetCalendarBorderDefault.md)|設定目前月曆控制項的框線的預設寬度。|  
|[CMonthCalCtrl::SetCalID](../Topic/CMonthCalCtrl::SetCalID.md)|設定目前月曆控制項的行事曆識別項。|  
|[CMonthCalCtrl::SetCenturyView](../Topic/CMonthCalCtrl::SetCenturyView.md)|設定目前月曆控制項顯示世紀檢視。|  
|[CMonthCalCtrl::SetColor](../Topic/CMonthCalCtrl::SetColor.md)|設定月曆控制項的指定範圍的色彩。|  
|[CMonthCalCtrl::SetCurrentView](../Topic/CMonthCalCtrl::SetCurrentView.md)|設定目前月曆控制項會顯示指定的檢視。|  
|[CMonthCalCtrl::SetCurSel](../Topic/CMonthCalCtrl::SetCurSel.md)|設定月曆控制項中目前選取的日期。|  
|[CMonthCalCtrl::SetDayState](../Topic/CMonthCalCtrl::SetDayState.md)|設定顯示在月曆控制項中的日期。|  
|[CMonthCalCtrl::SetDecadeView](../Topic/CMonthCalCtrl::SetDecadeView.md)|設定目前月曆控制項到十年檢視。|  
|[CMonthCalCtrl::SetFirstDayOfWeek](../Topic/CMonthCalCtrl::SetFirstDayOfWeek.md)|設定在日曆最左欄中顯示的星期。|  
|[CMonthCalCtrl::SetMaxSelCount](../Topic/CMonthCalCtrl::SetMaxSelCount.md)|設定月曆控制項中可選取的最多天數。|  
|[CMonthCalCtrl::SetMonthDelta](../Topic/CMonthCalCtrl::SetMonthDelta.md)|設定月曆控制項的捲動速率。|  
|[CMonthCalCtrl::SetMonthView](../Topic/CMonthCalCtrl::SetMonthView.md)|設定目前月曆控制項顯示月份檢視。|  
|[CMonthCalCtrl::SetRange](../Topic/CMonthCalCtrl::SetRange.md)|設定的最小，並允許的最大值為月曆控制項日期。|  
|[CMonthCalCtrl::SetSelRange](../Topic/CMonthCalCtrl::SetSelRange.md)|設定月曆控制項的選取範圍設定為特定日期範圍。|  
|[CMonthCalCtrl::SetToday](../Topic/CMonthCalCtrl::SetToday.md)|為目前的日期設定月曆控制項。|  
|[CMonthCalCtrl::SetYearView](../Topic/CMonthCalCtrl::SetYearView.md)|設定目前月曆控制項的檢視。|  
|[CMonthCalCtrl::SizeMinReq](../Topic/CMonthCalCtrl::SizeMinReq.md)|繪製月曆控制項為其最小，一個月的大小。|  
|[CMonthCalCtrl::SizeRectToMin](../Topic/CMonthCalCtrl::SizeRectToMin.md)|針對目前的月曆控制項，計算可以在指定的矩形包含所有曆法符合的最小矩形。|  
  
## 備註  
 月曆控制項為使用者提供一個簡單的行事曆介面，使用者可以選取日期。  使用者可以變更顯示:  
  
-   向前移動，在月份之間。  
  
-   按一下今天文字顯示目前日期 \(如果沒有使用 **MCS\_NOTODAY** 模式\)。  
  
-   選擇一個月或年份從快顯功能表。  
  
 您可以套用各種樣式自訂月曆控制項加入至物件，當您建立套件時。  這些模式是在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [月曆控制項模式。](http://msdn.microsoft.com/library/windows/desktop/bb760919) 說明。  
  
 月曆控制項可以顯示多個月份，，而且可以由 bolding 表示特殊日期 \(例如假日\) 日期。  
  
 如需使用月曆控制項的詳細資訊，請參閱 [使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## 需求  
 **Header:** afxdtctl.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL1](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl Class](../../mfc/reference/cdatetimectrl-class.md)