---
title: "CToolTipCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolTipCtrl class"
  - "data tips [C++]"
  - "工具提示 [C++], tool tip controls"
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝「工具提示控制項的功能，」顯示描述工具來說單行文字在應用程式的小型快顯視窗。  
  
## 語法  
  
```  
class CToolTipCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CToolTipCtrl::CToolTipCtrl](../Topic/CToolTipCtrl::CToolTipCtrl.md)|建構 `CToolTipCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CToolTipCtrl::Activate](../Topic/CToolTipCtrl::Activate.md)|啟動和停用工具提示控制項。|  
|[CToolTipCtrl::AddTool](../Topic/CToolTipCtrl::AddTool.md)|註冊工具提示控制項的工具。|  
|[CToolTipCtrl::AdjustRect](../Topic/CToolTipCtrl::AdjustRect.md)|在工具提示控制項的文字顯示矩形和其視窗的矩形之間轉換。|  
|[CToolTipCtrl::Create](../Topic/CToolTipCtrl::Create.md)|建立工具提示控制項並將其附加至 `CToolTipCtrl` 物件。|  
|[CToolTipCtrl::CreateEx](../Topic/CToolTipCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式之工具提示控制項並將其附加至 `CToolTipCtrl` 物件。|  
|[CToolTipCtrl::DelTool](../Topic/CToolTipCtrl::DelTool.md)|從工具提示控制項移除工具。|  
|[CToolTipCtrl::GetBubbleSize](../Topic/CToolTipCtrl::GetBubbleSize.md)|擷取工具提示的大小。|  
|[CToolTipCtrl::GetCurrentTool](../Topic/CToolTipCtrl::GetCurrentTool.md)|擷取資訊，例如大小、位置和文字目前工具提示控制項，顯示的工具提示視窗。|  
|[CToolTipCtrl::GetDelayTime](../Topic/CToolTipCtrl::GetDelayTime.md)|擷取針對工具提示控制項目前設定的初始、快顯 reshow 和持續期間。|  
|[CToolTipCtrl::GetMargin](../Topic/CToolTipCtrl::GetMargin.md)|擷取之前為工具提示視窗的頂端，設定，其左和右框線\)。|  
|[CToolTipCtrl::GetMaxTipWidth](../Topic/CToolTipCtrl::GetMaxTipWidth.md)|擷取工具提示視窗的最大寬度。|  
|[CToolTipCtrl::GetText](../Topic/CToolTipCtrl::GetText.md)|擷取工具提示控制項對工具所維護的文字。|  
|[CToolTipCtrl::GetTipBkColor](../Topic/CToolTipCtrl::GetTipBkColor.md)|擷取在工具提示視窗的背景色彩。|  
|[CToolTipCtrl::GetTipTextColor](../Topic/CToolTipCtrl::GetTipTextColor.md)|擷取在工具提示視窗的文字色彩。|  
|[CToolTipCtrl::GetTitle](../Topic/CToolTipCtrl::GetTitle.md)|擷取目前工具提示控制項的標題。|  
|[CToolTipCtrl::GetToolCount](../Topic/CToolTipCtrl::GetToolCount.md)|擷取工具提示控制項所維護之工具的計數。|  
|[CToolTipCtrl::GetToolInfo](../Topic/CToolTipCtrl::GetToolInfo.md)|擷取工具提示控制項維護有關工具的相關資訊。|  
|[CToolTipCtrl::HitTest](../Topic/CToolTipCtrl::HitTest.md)|測試點判斷它是否在指定之工具的週框內。  如果是的話，擷取與工具的相關資訊。|  
|[CToolTipCtrl::Pop](../Topic/CToolTipCtrl::Pop.md)|從檢視中移除一個顯示的工具提示視窗。|  
|[CToolTipCtrl::Popup](../Topic/CToolTipCtrl::Popup.md)|導致目前的工具提示控制項顯示最後一次滑鼠訊息的座標。|  
|[CToolTipCtrl::RelayEvent](../Topic/CToolTipCtrl::RelayEvent.md)|將滑鼠訊息處理的工具提示控制項。|  
|[CToolTipCtrl::SetDelayTime](../Topic/CToolTipCtrl::SetDelayTime.md)|設定中初始、快顯和 reshow 期間工具提示控制項的。|  
|[CToolTipCtrl::SetMargin](../Topic/CToolTipCtrl::SetMargin.md)|設定工具提示視窗的頂端，，其左和右框線\)。|  
|[CToolTipCtrl::SetMaxTipWidth](../Topic/CToolTipCtrl::SetMaxTipWidth.md)|設定工具提示視窗的最大寬度。|  
|[CToolTipCtrl::SetTipBkColor](../Topic/CToolTipCtrl::SetTipBkColor.md)|設定工具提示視窗的背景色彩。|  
|[CToolTipCtrl::SetTipTextColor](../Topic/CToolTipCtrl::SetTipTextColor.md)|設定工具提示視窗的文字色彩。|  
|[CToolTipCtrl::SetTitle](../Topic/CToolTipCtrl::SetTitle.md)|加入標準圖示和標題字串為工具提示。|  
|[CToolTipCtrl::SetToolInfo](../Topic/CToolTipCtrl::SetToolInfo.md)|設定工具提示的工具所維護的資訊。|  
|[CToolTipCtrl::SetToolRect](../Topic/CToolTipCtrl::SetToolRect.md)|設定工具建立新界限的矩形。|  
|[CToolTipCtrl::SetWindowTheme](../Topic/CToolTipCtrl::SetWindowTheme.md)|設定工具提示視窗的視覺化樣式。|  
|[CToolTipCtrl::Update](../Topic/CToolTipCtrl::Update.md)|強制現有工具重繪。|  
|[CToolTipCtrl::UpdateTipText](../Topic/CToolTipCtrl::UpdateTipText.md)|設定工具的工具提示文字。|  
  
## 備註  
 「工具」是一個視窗，例如子視窗或控制項用於在視窗工作區中的應用程式定義的矩形區域。  工具提示在大部分的情況中隱藏，才會顯示使用者在工具中將游標放置並提供限制一半一秒保留它的存在。  當使用者按一下滑鼠按鈕或移動游標，工具提示在游標周圍顯示或隱藏。  
  
 `CToolTipCtrl` 提供功能控制工具提示、框線寬度圍繞工具提示文字的開始時間和持續期間，寬度為工具提示視窗和工具提示的背景和文字色彩的。  單一工具提示控制項可以針對多個工具的相關資訊。  
  
 `CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。  這個控制項 \(也 `CToolTipCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需啟用工具提示的詳細資訊，請參閱 [在從 CFrameWnd 不衍生之視窗的工具提示。](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。  
  
 如需使用 `CToolTipCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)