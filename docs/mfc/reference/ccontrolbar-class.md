---
title: "CControlBar Class | Microsoft Docs"
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
  - "CControlBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CControlBar class"
  - "control bars [C++], 基底類別"
  - "dialog bars, 基底類別"
  - "OLE resize bars"
  - "OLE resize bars, 基底類別"
  - "狀態列, 基底類別"
  - "工具列 [C++], 基底類別"
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
caps.latest.revision: 22
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CControlBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制列的基底類別 [CStatusBar](../../mfc/reference/cstatusbar-class.md)、 [CToolBar](../../mfc/reference/ctoolbar-class.md)、 [CDialogBar](../../mfc/reference/cdialogbar-class.md)、 [CReBar](../../mfc/reference/crebar-class.md)、和 [COleResizeBar](../../mfc/reference/coleresizebar-class.md)。  
  
## 語法  
  
```  
class CControlBar : public CWnd  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CControlBar::CControlBar](../Topic/CControlBar::CControlBar.md)|建構 `CControlBar` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CControlBar::CalcDynamicLayout](../Topic/CControlBar::CalcDynamicLayout.md)|傳回做為 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件的動態控制列大小。|  
|[CControlBar::CalcFixedLayout](../Topic/CControlBar::CalcFixedLayout.md)|傳回做為 [CSize](../../atl-mfc-shared/reference/csize-class.md) 物件的控制列大小。|  
|[CControlBar::CalcInsideRect](../Topic/CControlBar::CalcInsideRect.md)|傳回控制列區域的目前大小 \(包含邊界\)。|  
|[CControlBar::DoPaint](../Topic/CControlBar::DoPaint.md)|呈現控制列的框線和移駐夾。|  
|[CControlBar::DrawBorders](../Topic/CControlBar::DrawBorders.md)|呈現控制列的框線。|  
|[CControlBar::DrawGripper](../Topic/CControlBar::DrawGripper.md)|呈現控制列的移駐夾。|  
|[CControlBar::EnableDocking](../Topic/CControlBar::EnableDocking.md)|允許將控制列停駐或浮動。|  
|[CControlBar::GetBarStyle](../Topic/CControlBar::GetBarStyle.md)|取得控制列的樣式設定。|  
|[CControlBar::GetBorders](../Topic/CControlBar::GetBorders.md)|取得控制列的邊界值。|  
|[CControlBar::GetCount](../Topic/CControlBar::GetCount.md)|在控制列將非`HWND` 的元素數目傳回。|  
|[CControlBar::GetDockingFrame](../Topic/CControlBar::GetDockingFrame.md)|傳回指向停駐控制列框架的的指標。|  
|[CControlBar::IsFloating](../Topic/CControlBar::IsFloating.md)|如果有問題的控制列是浮動控制列，則會傳回非零的值。|  
|[CControlBar::OnUpdateCmdUI](../Topic/CControlBar::OnUpdateCmdUI.md)|呼叫命令 UI 處理常式。|  
|[CControlBar::SetBarStyle](../Topic/CControlBar::SetBarStyle.md)|修改控制列的樣式設定。|  
|[CControlBar::SetBorders](../Topic/CControlBar::SetBorders.md)|設定控制列的邊界值。|  
|[CControlBar::SetInPlaceOwner](../Topic/CControlBar::SetInPlaceOwner.md)|變更控制列的就地擁有者。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CControlBar::m\_bAutoDelete](../Topic/CControlBar::m_bAutoDelete.md)|如果不為零，在 Windows 控制列被終結時，會同時刪除 `CControlBar` 物件。|  
|[CControlBar::m\_pInPlaceOwner](../Topic/CControlBar::m_pInPlaceOwner.md)|控制列的就地擁有者。|  
  
## 備註  
 一個控制列通常會對齊框架視窗的左邊或右邊。  它可以包含為視窗產生的 `HWND`子項目架構控制項 \(並回應 Windows 訊息\)，或者非 `HWND`\-基底項目 \(不是視窗，並由應用程式碼或架構程式碼處理\)。  清單方塊和編輯控制項是 `HWND`的範例架構控制項；狀態列窗格和點陣圖按鈕為非`HWND`的範例架構控制項。  
  
 控制列視窗通常是父框架視窗的子視窗，並通常是同層級對用戶端的檢視或框架視窗的 MDI 用戶端。  `CControlBar` 物件利用父視窗工作區矩形的資訊將自己當地語系化。  然後告知父視窗為父視窗工作區中的移除配置保留多少空間。  
  
 如需 `CControlBar` 的詳細資訊，請參閱：  
  
-   [控制列](../../mfc/control-bars.md)  
  
-   [Technical Note 31：控制列](../../mfc/tn031-control-bars.md)。  
  
-   知識庫文件 Q242577：PRB：更新命令讓 UI 處理常式不為附加至對話方塊的功能表工作  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## 需求  
 **標頭檔：**afxext.h  
  
## 請參閱  
 [MFC 範例 CTRLBARS](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar Class](../../mfc/reference/cdialogbar-class.md)   
 [CStatusBar Class](../../mfc/reference/cstatusbar-class.md)   
 [CReBar Class](../../mfc/reference/crebar-class.md)