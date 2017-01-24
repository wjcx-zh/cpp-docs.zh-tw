---
title: "COleControlContainer Class | Microsoft Docs"
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
  - "COleControlContainer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項容器 [C++], control site"
  - "COleControlContainer class"
  - "自訂控制項 [MFC], sites"
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControlContainer Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

做為控制項的 ActiveX 控制項容器。  
  
## 語法  
  
```  
class COleControlContainer : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleControlContainer::COleControlContainer](../Topic/COleControlContainer::COleControlContainer.md)|建構 `COleControlContainer` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleControlContainer::AttachControlSite](../Topic/COleControlContainer::AttachControlSite.md)|建立控制項站台，由裝載容器。|  
|[COleControlContainer::BroadcastAmbientPropertyChange](../Topic/COleControlContainer::BroadcastAmbientPropertyChange.md)|告知所有已裝載之控制項的環境屬性已變更。|  
|[COleControlContainer::CheckDlgButton](../Topic/COleControlContainer::CheckDlgButton.md)|修改指定的按鈕控制項。|  
|[COleControlContainer::CheckRadioButton](../Topic/COleControlContainer::CheckRadioButton.md)|選取群組中指定的選項按鈕。|  
|[COleControlContainer::CreateControl](../Topic/COleControlContainer::CreateControl.md)|建立裝載 ActiveX 控制項。|  
|[COleControlContainer::CreateOleFont](../Topic/COleControlContainer::CreateOleFont.md)|建立一個 OLE 字型。|  
|[COleControlContainer::FindItem](../Topic/COleControlContainer::FindItem.md)|傳回指定控制項的自訂網站。|  
|[COleControlContainer::FreezeAllEvents](../Topic/COleControlContainer::FreezeAllEvents.md)|判斷控制項的網站是否接受事件。|  
|[COleControlContainer::GetAmbientProp](../Topic/COleControlContainer::GetAmbientProp.md)|擷取指定的環境屬性。|  
|[COleControlContainer::GetDlgItem](../Topic/COleControlContainer::GetDlgItem.md)|擷取指定的對話方塊控制項。|  
|[COleControlContainer::GetDlgItemInt](../Topic/COleControlContainer::GetDlgItemInt.md)|擷取指定的對話方塊控制項的值。|  
|[COleControlContainer::GetDlgItemText](../Topic/COleControlContainer::GetDlgItemText.md)|擷取指定的對話方塊控制項的標題。|  
|[COleControlContainer::HandleSetFocus](../Topic/COleControlContainer::HandleSetFocus.md)|判斷容器是否處理 `WM_SETFOCUS` 訊息。|  
|[COleControlContainer::HandleWindowlessMessage](../Topic/COleControlContainer::HandleWindowlessMessage.md)|處理傳送給無視窗 \(Windowless\) 控制項。|  
|[COleControlContainer::IsDlgButtonChecked](../Topic/COleControlContainer::IsDlgButtonChecked.md)|判斷指定的按鍵的狀態。|  
|[COleControlContainer::OnPaint](../Topic/COleControlContainer::OnPaint.md)|呼叫以重新繪製容器的部分。|  
|[COleControlContainer::OnUIActivate](../Topic/COleControlContainer::OnUIActivate.md)|呼叫控制項時，會啟動就地編輯。|  
|[COleControlContainer::OnUIDeactivate](../Topic/COleControlContainer::OnUIDeactivate.md)|呼叫時，會停用控制項。|  
|[COleControlContainer::ScrollChildren](../Topic/COleControlContainer::ScrollChildren.md)|呼叫框架，在捲動訊息的子視窗接收。|  
|[COleControlContainer::SendDlgItemMessage](../Topic/COleControlContainer::SendDlgItemMessage.md)|將訊息傳送至指定的控制項。|  
|[COleControlContainer::SetDlgItemInt](../Topic/COleControlContainer::SetDlgItemInt.md)|設定指定控制項的值。|  
|[COleControlContainer::SetDlgItemText](../Topic/COleControlContainer::SetDlgItemText.md)|設定指定控制項的文字。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleControlContainer::m\_crBack](../Topic/COleControlContainer::m_crBack.md)|容器的背景色彩。|  
|[COleControlContainer::m\_crFore](../Topic/COleControlContainer::m_crFore.md)|容器的前景色彩。|  
|[COleControlContainer::m\_listSitesOrWnds](../Topic/COleControlContainer::m_listSitesOrWnds.md)|控制項支援的網站清單。|  
|[COleControlContainer::m\_nWindowlessControls](../Topic/COleControlContainer::m_nWindowlessControls.md)|裝載無視窗 \(Windowless\) 控制項數目。|  
|[COleControlContainer::m\_pOleFont](../Topic/COleControlContainer::m_pOleFont.md)|對自訂控制項站台的 OLE 字型的指標。|  
|[COleControlContainer::m\_pSiteCapture](../Topic/COleControlContainer::m_pSiteCapture.md)|會捕捉控制網站的指標。|  
|[COleControlContainer::m\_pSiteFocus](../Topic/COleControlContainer::m_pSiteFocus.md)|對目前擁有輸入焦點的控制項的指標。|  
|[COleControlContainer::m\_pSiteUIActive](../Topic/COleControlContainer::m_pSiteUIActive.md)|對目前就地啟動的控制項的指標。|  
|[COleControlContainer::m\_pWnd](../Topic/COleControlContainer::m_pWnd.md)|指標實作控制項容器的視窗。|  
|[COleControlContainer::m\_siteMap](../Topic/COleControlContainer::m_siteMap.md)|網站導覽。|  
  
## 備註  
 這是由支援執行的一或多個 ActiveX 控制項站台 \(實作 `COleControlSite`\)。  `COleControlContainer` 完整實作 [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770) 和 [IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103) 介面，允許從內容的 ActiveX 控制項完成其資格為就地項目。  
  
 通常，這個類別會使用 `COccManager` 和 `COleControlSite` 一起用來實作自訂 ActiveX 控制項容器中，有一或多個 ActiveX 控制項的自訂網站的。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## 需求  
 **Header:** afxocc.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleControlSite Class](../../mfc/reference/colecontrolsite-class.md)   
 [COccManager Class](../../mfc/reference/coccmanager-class.md)