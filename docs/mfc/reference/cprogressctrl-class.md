---
title: "CProgressCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CProgressCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CProgressCtrl class"
  - "Internet Explorer 4.0 common controls"
  - "progress controls [C++], CProgressCtrl class"
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CProgressCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 Windows 通用進度列控制項的功能。  
  
## 語法  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CProgressCtrl::CProgressCtrl](../Topic/CProgressCtrl::CProgressCtrl.md)|建構 `CProgressCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CProgressCtrl::Create](../Topic/CProgressCtrl::Create.md)|建立進度列控制項並將其附加至 `CProgressCtrl` 物件。|  
|[CProgressCtrl::CreateEx](../Topic/CProgressCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式之進度控制項並將其附加至 `CProgressCtrl` 物件。|  
|[CProgressCtrl::GetBarColor](../Topic/CProgressCtrl::GetBarColor.md)|取得進度列的色彩顯示目前進度列控制項。|  
|[CProgressCtrl::GetBkColor](../Topic/CProgressCtrl::GetBkColor.md)|取得目前進度列的背景色彩。|  
|[CProgressCtrl::GetPos](../Topic/CProgressCtrl::GetPos.md)|取得進度列的目前位置。|  
|[CProgressCtrl::GetRange](../Topic/CProgressCtrl::GetRange.md)|取得進度列控制項範圍的下限及上限。|  
|[CProgressCtrl::GetState](../Topic/CProgressCtrl::GetState.md)|取得目前進度列控制項的狀態。|  
|[CProgressCtrl::GetStep](../Topic/CProgressCtrl::GetStep.md)|擷取目前進度列控制項的進度列的步驟加入。|  
|[CProgressCtrl::OffsetPos](../Topic/CProgressCtrl::OffsetPos.md)|將指定的加入前移進度列控制項中目前的位置及重繪該列來反映新的位置。|  
|[CProgressCtrl::SetBarColor](../Topic/CProgressCtrl::SetBarColor.md)|設定進度列顯示的色彩在目前進度列控制項。|  
|[CProgressCtrl::SetBkColor](../Topic/CProgressCtrl::SetBkColor.md)|設定進度列的背景色彩。|  
|[CProgressCtrl::SetMarquee](../Topic/CProgressCtrl::SetMarquee.md)|關閉跑馬燈模式切換目前進度列控制項。|  
|[CProgressCtrl::SetPos](../Topic/CProgressCtrl::SetPos.md)|設定進度列控制項中目前的位置及重繪該列來反映新的位置。|  
|[CProgressCtrl::SetRange](../Topic/CProgressCtrl::SetRange.md)|設定進度列控制項的最小和最大範圍和重繪該列來反映新的範圍。|  
|[CProgressCtrl::SetState](../Topic/CProgressCtrl::SetState.md)|設定目前進度列控制項的狀態。|  
|[CProgressCtrl::SetStep](../Topic/CProgressCtrl::SetStep.md)|針對進度列控制項指定步驟加入。|  
|[CProgressCtrl::StepIt](../Topic/CProgressCtrl::StepIt.md)|藉由加入步驟前移進度列控制項的目前位置 \(請參閱\) [SetStep](../Topic/CProgressCtrl::SetStep.md)和重繪該列來反映新的位置。|  
  
## 備註  
 進度列控制項是應用程式可以使用指示長時間作業的進度的視窗。  它包括逐漸填滿，從左至右的矩形，與系統的醒目提示色彩，隨著作業的進度。  
  
 進度列控制項具有範圍和目前位置。  這個範圍表示作業的總持續期間，，而且目前的位置表示應用程式在作業上已完成的進度。  視窗程序會使用該範圍與目前位置判斷進度列的百分比以反白色彩填滿。  由於範圍和目前位置值會表示為帶正負號的整數，表示目前的位置值的範圍是從 2,147,483,648 到 2,147,483,647 –包含。  
  
 如需使用 `CProgressCtrl`的資訊，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## 需求  
 **標題:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL2](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)