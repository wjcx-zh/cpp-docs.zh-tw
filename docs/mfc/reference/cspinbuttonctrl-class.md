---
title: "CSpinButtonCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSpinButtonCtrl class"
  - "CSpinButtonCtrl class, 通用控制項"
  - "微調按鈕控制項"
  - "上下按鈕控制項, 微調按鈕控制項"
  - "Windows common controls [C++], CSpinButtonCtrl"
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSpinButtonCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用微調按鈕控制項的功能。  
  
## 語法  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](../Topic/CSpinButtonCtrl::CSpinButtonCtrl.md)|建構 `CSpinButtonCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSpinButtonCtrl::Create](../Topic/CSpinButtonCtrl::Create.md)|建立微調按鈕控制項並將其附加至 `CSpinButtonCtrl` 物件。|  
|[CSpinButtonCtrl::CreateEx](../Topic/CSpinButtonCtrl::CreateEx.md)|建立擁有指定之視窗的延伸樣式的微調按鈕控制項並將其附加至 `CSpinButtonCtrl` 物件。|  
|[CSpinButtonCtrl::GetAccel](../Topic/CSpinButtonCtrl::GetAccel.md)|擷取微調按鈕控制項的資訊。|  
|[CSpinButtonCtrl::GetBase](../Topic/CSpinButtonCtrl::GetBase.md)|擷取微調按鈕控制項的目前基底。|  
|[CSpinButtonCtrl::GetBuddy](../Topic/CSpinButtonCtrl::GetBuddy.md)|擷取目前項目的指標協同視窗。|  
|[CSpinButtonCtrl::GetPos](../Topic/CSpinButtonCtrl::GetPos.md)|擷取微調按鈕控制項的目前位置。|  
|[CSpinButtonCtrl::GetRange](../Topic/CSpinButtonCtrl::GetRange.md)|擷取的上限和下限 \(範圍\) 微調按鈕控制項。|  
|[CSpinButtonCtrl::SetAccel](../Topic/CSpinButtonCtrl::SetAccel.md)|設定微調按鈕控制項的加速。|  
|[CSpinButtonCtrl::SetBase](../Topic/CSpinButtonCtrl::SetBase.md)|設定微調按鈕控制項的基底。|  
|[CSpinButtonCtrl::SetBuddy](../Topic/CSpinButtonCtrl::SetBuddy.md)|設定微調按鈕控制項的協同視窗。|  
|[CSpinButtonCtrl::SetPos](../Topic/CSpinButtonCtrl::SetPos.md)|將控制項的目前位置。|  
|[CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md)|的上限和下限 \(範圍\) 微調按鈕控制項。|  
  
## 備註  
 「微調按鈕控制項」\(也稱為上下按鈕控制項\) 是一個讓使用者按一下加入或減去值的箭號按鈕，例如會顯示這個捲動位置或數字在附屬控制項。  值與微調按鈕控制項會呼叫其目前位置。  微調按鈕控制項最常配合附屬控制項，稱為「協同視窗」。  
  
 這個控制項 \(也 `CSpinButtonCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 對使用者來說，微調按鈕控制項和其協同視窗通常看起來像是單一控制項。  您可以指定微調按鈕控制項在其協同視窗旁。會自動將其本身定位，因此，它會自動設定協同視窗標題為其目前位置。  您可以使用微調按鈕控制項以編輯控制項提示數字中的使用者輸入。  
  
 按一下箭號會將目前的位置推向最大值，，然後按一下箭號向下移動目前的位置推向最小值。  根據預設，最小值為 100，最大值則為 0。  在最小安裝比最大設定大於 \(例如時，使用時，預設設定\) 時，按一下箭號減少位置值，然後按一下向下箭號將它。  
  
 沒有協同 Windows 函式的微調按鈕控制項做為一種簡化的捲軸。  例如，的索引標籤控制項 \(有時顯示微調按鈕控制項可讓使用者移動其他選項到檢視。  
  
 如需使用 `CSpinButtonCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl Class](../../mfc/reference/csliderctrl-class.md)