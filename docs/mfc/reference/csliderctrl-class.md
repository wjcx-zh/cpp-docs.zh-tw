---
title: "CSliderCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSliderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSliderCtrl class"
  - "CSliderCtrl class, 通用控制項"
  - "滑桿, CSliderCtrl class"
  - "Windows common controls [C++], CSliderCtrl"
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CSliderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用滑桿控制項的功能。  
  
## 語法  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSliderCtrl::CSliderCtrl](../Topic/CSliderCtrl::CSliderCtrl.md)|建構 `CSliderCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSliderCtrl::ClearSel](../Topic/CSliderCtrl::ClearSel.md)|清除  滑桿控制項的目前選取範圍。|  
|[CSliderCtrl::ClearTics](../Topic/CSliderCtrl::ClearTics.md)|從滑桿控制項中移除目前的刻度標記。|  
|[CSliderCtrl::Create](../Topic/CSliderCtrl::Create.md)|建立滑桿控制項並將其附加至 `CSliderCtrl` 物件。|  
|[CSliderCtrl::CreateEx](../Topic/CSliderCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的滑桿控制項並將其附加至 `CSliderCtrl` 物件。|  
|[CSliderCtrl::GetBuddy](../Topic/CSliderCtrl::GetBuddy.md)|擷取控制代碼滑桿控制項協同視窗是在指定的位置。|  
|[CSliderCtrl::GetChannelRect](../Topic/CSliderCtrl::GetChannelRect.md)|擷取通道滑桿控制項的大小。|  
|[CSliderCtrl::GetLineSize](../Topic/CSliderCtrl::GetLineSize.md)|擷取滑桿控制項的程式碼行大小。|  
|[CSliderCtrl::GetNumTics](../Topic/CSliderCtrl::GetNumTics.md)|擷取刻度標記數目滑桿控制項的。|  
|[CSliderCtrl::GetPageSize](../Topic/CSliderCtrl::GetPageSize.md)|擷取滑桿控制項的頁面大小。|  
|[CSliderCtrl::GetPos](../Topic/CSliderCtrl::GetPos.md)|擷取滑桿的目前位置。|  
|[CSliderCtrl::GetRange](../Topic/CSliderCtrl::GetRange.md)|擷取滑桿的最小值和最大值的位置。|  
|[CSliderCtrl::GetRangeMax](../Topic/CSliderCtrl::GetRangeMax.md)|擷取滑桿的位置最大值。|  
|[CSliderCtrl::GetRangeMin](../Topic/CSliderCtrl::GetRangeMin.md)|擷取滑桿的最小的位置。|  
|[CSliderCtrl::GetSelection](../Topic/CSliderCtrl::GetSelection.md)|擷取目前的選取範圍。|  
|[CSliderCtrl::GetThumbLength](../Topic/CSliderCtrl::GetThumbLength.md)|擷取滑桿的長度 \(以目前 TrackBar 控制項。|  
|[CSliderCtrl::GetThumbRect](../Topic/CSliderCtrl::GetThumbRect.md)|擷取滑桿控制項的捲動方塊的大小。|  
|[CSliderCtrl::GetTic](../Topic/CSliderCtrl::GetTic.md)|擷取指定的刻度標記的位置。|  
|[CSliderCtrl::GetTicArray](../Topic/CSliderCtrl::GetTicArray.md)|擷取滑桿控制項的刻度標記位置。|  
|[CSliderCtrl::GetTicPos](../Topic/CSliderCtrl::GetTicPos.md)|擷取指定的刻度標記的位置，在工作區座標中\)。|  
|[CSliderCtrl::GetToolTips](../Topic/CSliderCtrl::GetToolTips.md)|擷取控制代碼與工具提示控制項指派給滑桿控制項，，如果有的話。|  
|[CSliderCtrl::SetBuddy](../Topic/CSliderCtrl::SetBuddy.md)|指定視窗為滑桿控制項的協同視窗。|  
|[CSliderCtrl::SetLineSize](../Topic/CSliderCtrl::SetLineSize.md)|設定滑桿控制項的程式碼行大小。|  
|[CSliderCtrl::SetPageSize](../Topic/CSliderCtrl::SetPageSize.md)|設定滑桿控制項的頁面大小。|  
|[CSliderCtrl::SetPos](../Topic/CSliderCtrl::SetPos.md)|設定滑桿的目前位置。|  
|[CSliderCtrl::SetRange](../Topic/CSliderCtrl::SetRange.md)|設定滑桿的最小值和最大值的位置。|  
|[CSliderCtrl::SetRangeMax](../Topic/CSliderCtrl::SetRangeMax.md)|設定滑桿的位置最大值。|  
|[CSliderCtrl::SetRangeMin](../Topic/CSliderCtrl::SetRangeMin.md)|設定滑桿的最小的位置。|  
|[CSliderCtrl::SetSelection](../Topic/CSliderCtrl::SetSelection.md)|設定目前的選取範圍。|  
|[CSliderCtrl::SetThumbLength](../Topic/CSliderCtrl::SetThumbLength.md)|設定滑桿的長度 \(以目前 TrackBar 控制項。|  
|[CSliderCtrl::SetTic](../Topic/CSliderCtrl::SetTic.md)|設定指定的刻度標記的位置。|  
|[CSliderCtrl::SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md)|設定刻度的頻率每個滑桿控制項加入。|  
|[CSliderCtrl::SetTipSide](../Topic/CSliderCtrl::SetTipSide.md)|將 TrackBar 控制項使用的工具提示控制項。|  
|[CSliderCtrl::SetToolTips](../Topic/CSliderCtrl::SetToolTips.md)|指派工具提示控制項對滑桿控制項。|  
  
## 備註  
 「滑桿控制項」\(也稱為 TrackBar\) 是包含選擇性滑桿\) 和刻度標記的視窗。  當使用者移動滑桿時，使用滑鼠或方向鍵，控制項就會傳送通知訊息指出變更。  
  
 例如，當您想要使用者選取某個離散值或一組在範圍中時，的連續值滑桿控制項非常有用。  例如，您可以使用滑桿控制項可以讓使用者透過移動滑桿設定鍵盤的重複率移動至指定的刻度標記。  
  
 這個控制項 \(也 `CSliderCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 滑桿將指定的加入時加以建立。  例如，如果您指定，則滑桿應具有範圍的五個滑桿，只佔用六個定位:滑桿控制項左邊的位置和增量的位置範圍。  一般來說，這些位置都是由刻度標記所識別。  
  
 您建立滑桿使用建構函式並 `CSliderCtrl`的 **建立** 成員函式。  一旦建立滑桿控制項，您可以在 `CSliderCtrl` 可以使用成員函式來變更多項屬性。  變更可以包括設定滑桿的最小值和最大值的位置，繪製的刻度標記中，將選取範圍和位置滑桿。  
  
 如需使用 `CSliderCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl Class](../../mfc/reference/cprogressctrl-class.md)