---
title: "CReBar Class | Microsoft Docs"
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
  - "CReBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBar class"
  - "Internet Explorer 4.0 common controls"
  - "rebar controls, control bar"
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CReBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

針對 Rebar 控制項的配置、保存及狀態資訊的控制列。  
  
## 語法  
  
```  
  
class CReBar : public CControlBar  
  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CReBar::AddBar](../Topic/CReBar::AddBar.md)|將加入至 Rebar 群組列。|  
|[CReBar::Create](../Topic/CReBar::Create.md)|建立 Rebar 控制項並將其附加至 `CReBar` 物件。|  
|[CReBar::GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md)|允許傳送至基礎通用控制項的直接存取。|  
  
## 備註  
 Rebar 物件可以包含各種子視窗，通常是其他控制項，包括編輯方塊、工具列和清單方塊。  Rebar 物件可能會以指定的點陣圖的子視窗。  您的應用程式可以自動調整 Rebar，或者使用者可以按一下或拖曳的移駐夾列手動調整 Rebar 群組列。  
  
 ![RebarMenu 範例](../../mfc/reference/media/vc4sc61.png "vc4SC61")  
  
## Rebar 控制項  
 Rebar 物件具有類似的行為需工具列物件。  Rebar 使用按一下並拖曳機制來調整它的群組列。  Rebar 控制項可以包含一或多個群組列，而且每個群組列的移駐夾列、點陣圖、文字標籤和子視窗的任何組合。  不過，群組列不能包含一個以上的子視窗。  
  
 **CReBar** 使用 [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) 類別提供實作。  您可以 [GetReBarCtrl](../Topic/CReBar::GetReBarCtrl.md) 存取 Rebar 控制項使用控制項的自訂選項。  如需 Rebar 控制項的詳細資訊，請參閱 `CReBarCtrl`。  如需使用 Rebar 控制項的詳細資訊，請參閱 [使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
> [!CAUTION]
>  Rebar 和 Rebar 控制項物件不支援 MFC 控制列停駐。  如果 **CRebar::EnableDocking** 呼叫，您的應用程式會判斷提示。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [MFC 範例 MFCIE](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)