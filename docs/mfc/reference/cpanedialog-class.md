---
title: "CPaneDialog Class | Microsoft Docs"
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
  - "CPaneDialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneDialog class"
  - "CPaneDialog constructor"
  - "CPaneDialog::CreateObject method"
  - "CPaneDialog::OnEraseBkgnd method"
  - "CPaneDialog::OnLButtonDblClk method"
  - "CPaneDialog::OnLButtonDown method"
  - "CPaneDialog::OnUpdateCmdUI method"
  - "CPaneDialog::OnWindowPosChanging method"
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
caps.latest.revision: 27
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPaneDialog Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPaneDialog` 類別支援非強制回應對話方塊，可停駐  對話方塊。  
  
## 語法  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CPaneDialog::CPaneDialog`|預設建構函式。|  
|`CPaneDialog::~CPaneDialog`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPaneDialog::Create](../Topic/CPaneDialog::Create.md)|建立可停駐對話方塊並將其附加至 `CPaneDialog` 物件。|  
|`CPaneDialog::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|`CPaneDialog::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CPaneDialog::HandleInitDialog](../Topic/CPaneDialog::HandleInitDialog.md)|處理 [WM\_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) 訊息。  \(重新定義 `CBasePane::HandleInitDialog`\)。|  
|`CPaneDialog::OnEraseBkgnd`|處理 [WM\_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) 訊息。  \(重新定義 [CWnd::OnEraseBkgnd](../Topic/CWnd::OnEraseBkgnd.md)\)。|  
|`CPaneDialog::OnLButtonDblClk`|處理 [WM\_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) 訊息。  \(重新定義 [CWnd::OnLButtonDblClk](../Topic/CWnd::OnLButtonDblClk.md)\)。|  
|`CPaneDialog::OnLButtonDown`|處理 [WM\_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607) 訊息。  \(重新定義 [CWnd::OnLButtonDown](../Topic/CWnd::OnLButtonDown.md)\)。|  
|`CPaneDialog::OnUpdateCmdUI`|呼叫框架更新對話方塊視窗。  \(覆寫 [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/zh-tw/5dd61606-1c12-40d4-b024-f3839aa5e2e0)\)。|  
|`CPaneDialog::OnWindowPosChanging`|處理 [WM\_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653) 訊息。  \(重新定義 [CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)\)。|  
|[CPaneDialog::SetOccDialogInfo](../Topic/CPaneDialog::SetOccDialogInfo.md)|為 OLE 控制項容器的對話方塊中指定範本。|  
  
## 備註  
 建構以兩個步驟的 `CPaneDialog` 物件。  首先，請建構物件至程式碼。  接著，呼叫 [CPaneDialog::Create](../Topic/CPaneDialog::Create.md)。  您必須指定有效的資源樣板或樣板名稱和 ID 將指標傳遞至父視窗。  否則，建立程序失敗。  對話方塊必須指定 WS\_CHILD 和 WS\_VISIBLE，0x1000 樣式。  建議您同時指定和 WS\_CLIPSIBLINGS WS\_CLIPCHILDREN 樣式。  如需詳細資訊，請參閱 [視窗樣式](../../mfc/reference/window-styles.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## 需求  
 **標題:** afxpanedialog.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [視窗樣式](../../mfc/reference/window-styles.md)