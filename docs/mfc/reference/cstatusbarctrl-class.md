---
title: "CStatusBarCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl class"
  - "status bar controls"
  - "Windows common controls [C++], CStatusBarCtrl"
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CStatusBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用狀態列控制項的功能。  
  
## 語法  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CStatusBarCtrl::CStatusBarCtrl](../Topic/CStatusBarCtrl::CStatusBarCtrl.md)|建構 `CStatusBarCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStatusBarCtrl::Create](../Topic/CStatusBarCtrl::Create.md)|建立狀態列控制項並將其附加至 `CStatusBarCtrl` 物件。|  
|[CStatusBarCtrl::CreateEx](../Topic/CStatusBarCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的狀態列控制項並將其附加至 `CStatusBarCtrl` 物件。|  
|[CStatusBarCtrl::DrawItem](../Topic/CStatusBarCtrl::DrawItem.md)|呼叫，以主控描繪狀態列控制項的視覺外觀變更時。|  
|[CStatusBarCtrl::GetBorders](../Topic/CStatusBarCtrl::GetBorders.md)|擷取狀態列控制項的水平和垂直框線的目前寬度。|  
|[CStatusBarCtrl::GetIcon](../Topic/CStatusBarCtrl::GetIcon.md)|擷取一個部分 \(也稱為窗格\) 圖示目前狀態列控制項。|  
|[CStatusBarCtrl::GetParts](../Topic/CStatusBarCtrl::GetParts.md)|擷取部分的計數在狀態列控制項的。|  
|[CStatusBarCtrl::GetRect](../Topic/CStatusBarCtrl::GetRect.md)|擷取一個部分的週框 \(Bounding Rectangle\) 狀態列控制項的。|  
|[CStatusBarCtrl::GetText](../Topic/CStatusBarCtrl::GetText.md)|從狀態列控制項的指定區段擷取文字。|  
|[CStatusBarCtrl::GetTextLength](../Topic/CStatusBarCtrl::GetTextLength.md)|從狀態列控制項的指定區段擷取長度，以字元，文字。|  
|[CStatusBarCtrl::GetTipText](../Topic/CStatusBarCtrl::GetTipText.md)|擷取一個窗格的工具提示文字在狀態列。|  
|[CStatusBarCtrl::IsSimple](../Topic/CStatusBarCtrl::IsSimple.md)|檢查狀態視窗控制項判斷它是否在簡單模式。|  
|[CStatusBarCtrl::SetBkColor](../Topic/CStatusBarCtrl::SetBkColor.md)|設定在狀態列的背景色彩。|  
|[CStatusBarCtrl::SetIcon](../Topic/CStatusBarCtrl::SetIcon.md)|設定一個窗格的圖示會出現在狀態列。|  
|[CStatusBarCtrl::SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md)|設定狀態列控制項的繪製區域的最小高度。|  
|[CStatusBarCtrl::SetParts](../Topic/CStatusBarCtrl::SetParts.md)|設定區段數目狀態列控制項的每個部分和右邊緣的座標。|  
|[CStatusBarCtrl::SetSimple](../Topic/CStatusBarCtrl::SetSimple.md)|指定狀態列控制項是否顯示簡單文字或顯示先前呼叫方法所設定的任何控制項的組件。 `SetParts`。|  
|[CStatusBarCtrl::SetText](../Topic/CStatusBarCtrl::SetText.md)|將狀態列控制項的指定區段中的文字。|  
|[CStatusBarCtrl::SetTipText](../Topic/CStatusBarCtrl::SetTipText.md)|設定一個窗格的工具提示文字在狀態列。|  
  
## 備註  
 「狀態列控制項」是一個水平視窗，通常是顯示在父視窗的底部，應用程式可以在其中顯示各種狀態資訊。  狀態列控制項可分成兩部分顯示一個以上的資訊類型。  
  
 這個控制項 \(也 `CStatusBarCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需使用 `CStatusBarCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl Class](../../mfc/reference/ctoolbarctrl-class.md)